---
description: Control aspects of your trmnl.com account
---

# Account API

In addition to the [device API](screens.md), TRMNL has an account API. You can enumerate your devices, import and export plugins, control playlists, and more -- see [More Endpoints](more-endpoints.md) for the full map.

See the [**OpenAPI specification**](https://trmnl.com/api-docs) for complete details.

We have also open-sourced an official [**trmnl-api**](https://github.com/usetrmnl/trmnl-api) Ruby gem for API clients.

Prefer the command line? The [**TRMNL CLI**](cli.md) turns every endpoint into a command. It signs in through your browser, or set `TRMNL_API_KEY` to your account API key for scripts and CI.

```
brew install usetrmnl/tap/trmnl
trmnl list-devices
```

{% hint style="info" %}
These endpoints are being continually improved upon as we discover new use-cases, so please send us feedback with your API feature requests.
{% endhint %}

## Authentication

Every request sends a bearer token in the HTTP Authorization header, e.g. `Authorization: Bearer trmnl_xxxxx`. There are two ways to get one.

### Account API keys

Create keys from [your account settings](https://trmnl.com/account) under Account API keys. This section appears once your account has a device with the [Developer edition](https://shop.trmnl.com/products/developer-edition) upgrade (every [BYOD license](https://shop.trmnl.com/products/byod) includes it). Keys begin with `trmnl_` and are shown once, so copy yours somewhere safe.

**Each key only does what you allow it to.** Pick one or more capabilities when you create it:

| Capability | What it allows                                                                                  |
| ---------- | ----------------------------------------------------------------------------------------------- |
| `read`     | List + read devices, playlists, plugin settings, markup, logs, recipes                          |
| `content`  | Create + edit plugin settings, markup, plugin data + fields, playlists, mashups                 |
| `devices`  | Change device settings, claim, identify, mirror                                                 |
| `delete`   | Delete plugin settings, playlist items, themes, app installations                               |
| `profile`  | Read + update your user profile (`/api/me`)                                                     |
| `apps`     | Install apps, and manage Fleet + Room Booking (bookings included)                              |

You can also limit a key to some devices and plugin settings. A request outside a key's capabilities or limits answers `403` with a message naming what's missing. Revoke a key from the same page at any time -- other keys keep working.

{% hint style="warning" %}
**Legacy key.** The same page also shows a "Legacy account API key" beginning with `user_`. It still works, but only on the endpoints it had back then (devices, playlist items, plugin settings + their data, markup and archives, `/api/me`). Everything newer answers `403`. Create a `trmnl_` key instead.
{% endhint %}

### Connected apps (OAuth)

Building something other people will sign in to? **Don't ask people for their API key.** Register an app at [trmnl.com/developer\_apps](https://trmnl.com/developer_apps) (any account with a device) and use the OAuth authorization code flow with PKCE. Users pick the same capabilities as scopes, can limit the connection to some devices and plugin settings, and revoke it under Account > Connected agents. Walkthrough: [Connect with TRMNL](https://help.trmnl.com/en/articles/17225165-connect-with-trmnl-developer-apps). Full protocol: [trmnl.com/auth.md](https://trmnl.com/auth.md).

## Rate limits

Each account gets 120 requests per minute across the whole account API, 300 with TRMNL+. Over that you get a `429` with `{"error": "Rate limit exceeded. Maximum 120 requests per minute."}`.

Failed authentications are limited to 20 per minute per IP address.

## Example

```javascript
// GET https://trmnl.com/api/devices (trimmed, see the spec for every field)

{
  "data": [
    {
      "id": 123456,
      "name": "My TRMNL",
      "friendly_id": "A1B2C3",
      "mac_address": "••:••:••:••:34:56",
      "firmware_version": "1.7.1",
      "battery_voltage": 3.9,
      "percent_charged": 85.0,
      "rssi": -41,
      "wifi_strength": 75.0,
      "refresh_interval": 900,
      "last_ping_at": "2026-09-29T14:30:00.000Z"
    }
  ]
}
```

Successful responses wrap the result in `data`. Errors come back as `{"error": "..."}` with a matching HTTP status. A `trmnl_` key or connected app sees only the last two bytes of each MAC address.
