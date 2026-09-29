---
description: OAuth installation flow between TRMNL and your web server.
---

# Plugin Installation Flow

<figure><img src="../.gitbook/assets/plugin-installation-flow.svg" alt="Plugin installation flow between TRMNL and your web server"><figcaption></figcaption></figure>

Third Party plugins use a simplified OAuth2 flow. The token exchange needs no `client_id` or `client_secret` -- TRMNL identifies your plugin by the URLs you registered during [Plugin Creation](plugin-creation.md), and each installation is authorized by a `code`. (Your Client ID does matter later, to verify the [management flow](plugin-management-flow.md) JWT.)

1. **Installation Request**

When a user installs your plugin, TRMNL redirects their browser to your `installation_url`. This is a `GET` request, so both parameters arrive in the query string (URL-encoded):

* `code` — an installation code for this user + plugin. If the user abandons the flow and starts again, they arrive with the same code
* `installation_callback_url` — the TRMNL URL you send the user back to once installation is complete (see Step 4). Treat it as opaque -- it may carry extra params, like a `playlist_item_id`

```bash
GET 'https://your-server.com/your-installation-url?code=abc123&installation_callback_url=https%3A%2F%2Ftrmnl.com%2Fplugin_settings%2Fnew%3Fkeyname%3Dyour_plugin%26code%3Dabc123'
```

2. **Fetch Access Token**

Exchange the `code` from Step 1 for an `access_token` by sending a `POST` request to TRMNL's token endpoint. The `code` is the only parameter required, sent as a form-encoded body:

```bash
curl -XPOST 'https://trmnl.com/oauth/token' \
-H 'Content-Type: application/x-www-form-urlencoded' \
-d 'code=abc123'
```

3. **Access Token**

TRMNL responds with a JSON body containing the `access_token`. Persist this token -- TRMNL sends it as the Bearer token on every [screen generation](plugin-screen-generation-flow.md) request and webhook, so you can match each request to this installation. The token doesn't expire and there's no refresh step. Exchanging the same `code` again returns the same token.

```json
{ "access_token": "a1b2c3d4e5f6..." }
```

If the `code` is missing or invalid, TRMNL responds with an error body instead (note: the HTTP status is still `200`):

```json
{ "error": true, "message": "invalid code" }
```

4. **Installation Callback**

Redirect the user's browser to the `installation_callback_url` you received in Step 1. This `GET` redirect returns them to TRMNL's new plugin instance form, where they can name the instance, then click **Save**. The installation isn't complete until they save.

```bash
GET '<installation_callback_url>'
```

5. **Success Webhook**

When the user clicks **Save** in Step 4, TRMNL sends a `POST` request to your `installation_success_webhook_url`. The request is authenticated with the user's `access_token` and the body is JSON. We send it once, with no retries.

{% hint style="warning" %}
Exchange the `code` (Step 2) before redirecting the user back. If no `access_token` exists yet when they save, TRMNL sends this webhook without an `Authorization` header.
{% endhint %}

HTTP Headers:

```
Authorization: Bearer <access_token>
Content-Type: application/json
```

Body:

```json
{
  "user": {
    "id":5678,
    "name":"Ronak J",
    "email":"ronak@trmnl.com",
    "first_name":"Ronak",
    "last_name":"J",
    "locale":"en",
    "time_zone":"Pacific Time (US & Canada)",
    "time_zone_iana":"America/Los_Angeles",
    "utc_offset":-28800,
    "plugin_setting_id":1234,
    "uuid": "674c9d99-cea1-4e52-9025-9efbe0e30901"
  }
}
```

Time zone mappings are available here under "Constants:"\
[https://api.rubyonrails.org/classes/ActiveSupport/TimeZone.html](https://api.rubyonrails.org/classes/ActiveSupport/TimeZone.html)

The `plugin_setting_id`is useful for building a redirect URI in your own application, for example to send a user back to trmnl.com/plugin\_settings/:plugin\_setting\_id/edit.
