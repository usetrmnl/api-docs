---
description: OAuth installation flow between TRMNL and your web server.
---

# Plugin Installation Flow

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

1. **Installation Request**

When the user installs your plugin, TRMNL sends an installation request to `installation_url` with unique `token` and `installation_callback_url`.

2. **Fetch Access Token**

After receiving the request, Your server using the `client_id`, `client_secret` and `token` from step#1 request the `access_token` from TRMNL using the following endpoint:

```bash
body = {
  code: 'code-from-step-1',
  client_id: 'your-plugin-client-id',
  client_secret: 'your-plugin-secret',
  grant_type: 'authorization_code'
}
response = HTTParty.post("https://usetrmnl.com/oauth/token", body: body)
response['access_token']
```

3. **Access Token**

TRMNL responds with the `access_token`.

4. **Installation Callback**

Use the `installation_callback_url` from Step #1 and redirect the user back to TRMNL.

5. **Success Webhook**

After the user has successfully finished installing the plugin, TRMNL sends a POST success notification to `installation_success_webhook_url` endpoint. Data is sent in JSON format as follows.

HTTP Headers:

```bash
{'Authorization': 'Bearer <access_token>', 'Content-Type': 'application/json'}
```

Body:

```json
{
  "user": {
    "name":"Ronak J",
    "email":"ronak@usetrmnl.com",
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

The `plugin_setting_id`is useful for building a redirect URI in your own application, for example to send a user back to usetrmnl.com/plugin\_settings/:plugin\_setting\_id/edit.
