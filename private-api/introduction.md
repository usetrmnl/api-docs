---
description: Advanced features available for Developer edition devices.
---

# Introduction

As outlined in our [open source firmware](https://github.com/usetrmnl/firmware), TRMNL exposes a GET endpoint that responds with image and other content for your device to store or render.

```
GET /api/display

# request headers example
{
  'ID' => 'XX:XX:XX:XX',
  'Access-Token' => '2r--SahjsAKCFksVcped2Q'
}

# response body example
{
  "image_url"=>"https://trmnl.s3.us-east-2.amazonaws.com/path-to-img.bmp",
  "image_name"=>"2024-09-20T00:00:00",
  "update_firmware"=>false,
}
```

The TRMNL server leverages your device's immutable Mac Address (`ID` ) header during initial setup, then depends on the `Access-Token`header for subsequent requests.

Thus, **if you know your device's API key, you can request content without a TRMNL device or TRMNL firmware**.

In these \[WIP] Private API docs we'll outline a few ways to take advantage of this information for your own privacy, security, and experimentation purposes.

{% hint style="info" %}
**Only devices with the Developer add-on** may access their own Access Token. You may unlock this feature anytime from your [Devices > Edit](https://usetrmnl.com/devices/) page for a one-time fee.
{% endhint %}

