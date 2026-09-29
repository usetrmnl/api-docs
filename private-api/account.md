---
description: Control aspects of your trmnl.com account
---

# Account API

In addition to the [device API](screens.md), users who have purchased a developer license can access the account API. You can enumerate your devices, import and export plugins, control playlists, and more.

See the [**OpenAPI specification**](https://trmnl.com/api-docs) for complete details.

We have also open-sourced an official [**trmnl-api**](https://github.com/usetrmnl/trmnl-api) Ruby gem for API clients.

Prefer the command line? The [**TRMNL CLI**](https://github.com/usetrmnl/cli) turns every endpoint into a command. It signs in through your browser, or set `TRMNL_API_KEY` to your account API key for scripts and CI.

```
brew install usetrmnl/tap/trmnl
trmnl list-devices
```

{% hint style="info" %}
These endpoints are being continually improved upon as we discover new use-cases, so please send us feedback with your API feature requests.
{% endhint %}

## Authentication

Create an API key from [your account settings](https://trmnl.com/account), under Account API keys. Each key begins with `trmnl_` and is shown once, so copy it before you leave the page.

When you create a key you pick what it can do: `read`, `content`, `devices`, `delete`, `profile` or `apps`. You can also limit it to some devices and plugin settings. A request outside those answers `403` and names what the key is missing. Revoking a key revokes only that key.

Send the key as a bearer token in the HTTP Authorization header, e.g. `Authorization: Bearer trmnl_xxxxx`

{% hint style="info" %}
The older account API key, which begins with `user_`, still works but only reaches the endpoints it had before keys held capabilities. Anything newer answers `403`.
{% endhint %}

### Building an app other people connect to?

Don't ask people for their API key. Register a developer app at [trmnl.com/developer\_apps](https://trmnl.com/developer_apps) and let them connect through the OAuth consent screen instead. The access token it returns works on these same endpoints. See the [Connect with TRMNL guide](https://help.trmnl.com/en/articles/17225165-connect-with-trmnl-developer-apps) and [auth.md](https://trmnl.com/auth.md).

## Example

```javascript
// GET https://trmnl.com/api/devices

{
  "data": [
    {
      "id": 123456,
      "name": "My TRMNL",
      "friendly_id": "A1B2C3",
      "mac_address": "••:••:••:••:56:78",
      "battery_voltage": 3.9,
      "rssi": -41
    }
  ]
}
```

All but the last two bytes of `mac_address` are masked for an API key or a connected app.
