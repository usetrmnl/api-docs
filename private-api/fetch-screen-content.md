---
description: Retrieve TRMNL image data, device-free.
---

# Fetch Screen Content

First, set up a TRMNL device or [BYOD license](https://shop.usetrmnl.com/products/byod).

Next, grab your API Key from [Devices > Edit](https://usetrmnl.com/devices) and make a request like below.

### Auto advance content

This endpoint is used by our firmware (on your device) to fetch new screen content. Making a request to this endpoint automatically 'advances' your Playlist to the next item in your queue. To simply grab the current screen instead, skip to the next section below.

```
curl https://usetrmnl.com/api/display --header "access-token:xxxxxx"
```

This will respond with several fields, for example:

```
{
  "status"=>0, # will be 202 if no user_id is attached to device
  "image_url"=>"https://trmnl.s3.us-east-2.amazonaws.com/path-to-img.png",
  "image_name"=>"plugin-YYYY-MM-DD-TXX-XX-XXZ-hash",
  "update_firmware"=>false,
  "firmware_url"=>nil,
  "refresh_rate"=>"1800",
  "reset_firmware"=>false
}
```

The `image_url` is likely the most interesting to you, as this may be leveraged by your own hardware to render content however you see fit.

{% hint style="info" %}
**Note**: TRMNL devices send a few additional values in the request headers by default, such as your WiFi connection strength (RSSI value), firmware version (ex: 1.3.7), and more.&#x20;

These attributes impact the response content by instructing the device to either update firmware, change its refresh rate, and so on. But excluding these values from your request is OK, just be aware that some response values may be nil.
{% endhint %}

### Current screen

If you're expanding a TRMNL fleet with BYOD devices, such as a [Raspberry Pi](https://usetrmnl.com/blog/rpi-trmnl) or [Kindle](https://usetrmnl.com/guides/turn-your-amazon-kindle-into-a-trmnl), [Android](https://github.com/usetrmnl/trmnl-android), or [Kobo](https://github.com/usetrmnl/trmnl-kobo) tablet, you may prefer to mirror whatever content is showing on your official TRMNL or BYOD device.

```
curl https://usetrmnl.com/api/current_screen --header "access-token:xxxxxx"
```

This will respond with the following fields:

```
{"status" => 200,
 "refresh_rate" => 1800,
 "image_url" => "https://usetrmnl.com/rails/active_storage/blobs/redirect/hash-here/plugin-YYYY-MM-DD-TXX-XX-XXZ-hash",
 "filename" => "plugin-YYYY-MM-DD-TXX-XX-XXZ-hash",
 "rendered_at" => nil
 }
```

{% hint style="info" %}
**Note**: the `current_screen` endpoint was designed for consumption by our [Chrome extension](https://usetrmnl.com/chrome). Please don't abuse it.
{% endhint %}
