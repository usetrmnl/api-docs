---
description: Retrieve TRMNL image data, device-free.
---

# Fetch Screen Content

First, set up a TRMNL device with the [Developer edition](https://shop.trmnl.com/products/developer-edition) upgrade, or a [BYOD license](https://shop.trmnl.com/products/byod).

Next, grab your device API key from [Devices](https://trmnl.com/devices) > Edit > Developer perks and make a request like below.

### Auto advance content

This endpoint is used by our firmware (on your device) to fetch new screen content. Making a request to this endpoint automatically 'advances' your Playlist to the next item in your queue. To simply grab the current screen instead, skip to the next section below.

```
curl https://trmnl.com/api/display --header "access-token:xxxxxx"
```

This will respond with several fields, for example:

```
{
  "status": 0,                # 202 if no user is attached to the device yet
  "image_url": "https://.../plugin-2026-09-29T21:57:33Z-90f0f9.png",
  "filename": "plugin-2026-09-29T21:57:33Z-90f0f9",
  "refresh_rate": 1800,       # seconds until the next request
  "reset_firmware": false,
  "update_firmware": false,
  "firmware_url": "",         # a download link when update_firmware is true
  "special_function": "identify" # what the device button does
}
```

The `image_url` is likely the most interesting to you, as this may be leveraged by your own hardware to render content however you see fit. Send a `base64: true` header to get the image bytes base64-encoded inside `image_url` instead of a link.

{% hint style="info" %}
**Note**: TRMNL devices send a few additional values in the request headers by default, such as your WiFi connection strength (`RSSI`), firmware version (`FW-Version`, ex: 1.7.1), battery voltage, screen `Width` + `Height`, and more. The full list is in the [OpenAPI spec](https://trmnl.com/api-docs).

These attributes impact the response content by instructing the device to either update firmware, change its refresh rate, and so on. Newer firmware versions also get extra fields like `maximum_compatibility` and `temperature_profile`. Excluding these headers from your request is OK, just be aware that some response values may be empty.
{% endhint %}

After setup, each device gets 40 requests to `/api/display` per 5 minutes. Past that we answer with a "rate limited" system screen and a 5-15 minute `refresh_rate` instead of your content.

{% hint style="warning" %}
A request with an unknown `access-token` answers `{"status": 500, "error": "Device not found", "reset_firmware": true}`. Our firmware reads that as "erase WiFi credentials + API key", so double check the key before pointing real hardware at it.
{% endhint %}

### Current screen

If you're expanding a TRMNL fleet with BYOD devices, such as a [Raspberry Pi](https://trmnl.com/blog/rpi-trmnl) or [Kindle](https://trmnl.com/guides/turn-your-amazon-kindle-into-a-trmnl), [Android](https://github.com/usetrmnl/trmnl-android), or [Kobo](https://github.com/usetrmnl/trmnl-kobo) tablet, you may prefer to mirror whatever content is showing on your official TRMNL or BYOD device. This endpoint does not advance the Playlist.

```
curl https://trmnl.com/api/display/current --header "access-token:xxxxxx"
```

This will respond with the following fields:

```
{
  "status": 200,
  "refresh_rate": 1800,
  "image_url": "https://.../plugin-2026-09-29T21:57:33Z-90f0f9.png",
  "filename": "plugin-2026-09-29T21:57:33Z-90f0f9"
}
```

If nothing has been displayed yet you'll get `{"status": 404, "message": "No screen currently being displayed"}`. The older `/api/current_screen` path still works and returns the same thing.

{% hint style="info" %}
**Note**: the current screen endpoint was designed for consumption by our [Chrome extension](https://trmnl.com/chrome) and allows 6 requests per minute per device. Please don't abuse it.
{% endhint %}

Want device health, logs, or playlist control instead of images? That's the [Account API](account.md).
