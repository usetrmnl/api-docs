---
description: Advanced features available for Developer edition devices.
---

# Introduction

{% hint style="info" %}
Every endpoint, parameter + response shape lives in our [API reference](https://trmnl.com/api-docs), generated from our code + always current.
{% endhint %}

As outlined in our [open source firmware](https://github.com/usetrmnl/firmware), TRMNL exposes a GET endpoint that responds with image and other content for your device to store or render.

```
GET /api/display

# request headers example
{
  'Access-Token' => '2r--SahjsAKCFksVcped2Q'
}

# response body example
{
  "status": 0,
  "image_url": "https://.../plugin-2026-09-29T21:57:33Z-90f0f9.png",
  "filename": "plugin-2026-09-29T21:57:33Z-90f0f9",
  "refresh_rate": 900,
  "update_firmware": false,
  "reset_firmware": false
}
```

**With a device's API key you can request content without a TRMNL device or TRMNL firmware**.

Your device API key lives in [Devices](https://trmnl.com/devices) > Edit > Developer perks. That section requires the [Developer edition](https://shop.trmnl.com/products/developer-edition) upgrade -- every [BYOD license](https://shop.trmnl.com/products/byod) ships with it.

In the following Private API docs we'll outline a few ways to take advantage of this information for your own privacy, security, and experimentation purposes:

* [Display API](screens.md) -- fetch the next or current screen with a device API key
* [Plugin Data API](plugin-data.md) -- reuse the JSON behind any plugin in your own markup
* [Account API](account.md) -- manage devices, playlists + plugins with an account API key or a connected app
* [More Endpoints](more-endpoints.md) -- a map of everything the account API covers

{% hint style="info" %}
**One key per job.** A device API key reaches only that device's screens. An account API key (`trmnl_...`) reaches your account. Don't mix them up -- a request to `/api/display` with an unknown key tells the device to erase its WiFi credentials + API key.
{% endhint %}
