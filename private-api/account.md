---
description: Control aspects of your trmnl.com account
---

# Account API

In addition to the [device API](screens.md), users who have purchased a developer license can access the account API. You can enumerate your devices, import and export plugins, control playlists, and more.

See the [**OpenAPI specification**](https://trmnl.com/api-docs/index.html) for complete details.

We have also open-sourced an official [**trmnl-api**](https://github.com/usetrmnl/trmnl-api) Ruby gem for API clients.

{% hint style="info" %}
These endpoints are being continually improved upon as we discover new use-cases, so please send us feedback with your API feature requests.
{% endhint %}

## Authentication

The account API key can be retrieved from [your account settings](https://trmnl.com/account). It begins with `user_`.

API authentication is done via the HTTP Authorization header with bearer tokens, e.g. `Authorization: Bearer user_xxxxx`

## Example

```javascript
// GET https://trmnl.com/api/devices

{
  "data": [
    {
      "id": 123456,
      "name": "My TRMNL",
      "friendly_id": "A1B2C3",
      "mac_address": "AB:CD:EF:12:34:56",
      "battery_voltage": 3.9,
      "rssi": -41
    }
  ]
}
```
