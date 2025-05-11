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
  "filename"=>"2025-05-10-plugin-T00:00:00",
  "update_firmware"=>false
}
```

**With a device's API key you can request content without a TRMNL device or TRMNL firmware**.

In the following Private API docs we'll outline a few ways to take advantage of this information for your own privacy, security, and experimentation purposes.
