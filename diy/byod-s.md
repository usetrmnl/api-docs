---
description: Bring your own device, and build your own server for the device to ping.
---

# BYOD/S

In the BYOD/S model, the only TRMNL IP is our [open source firmware](https://github.com/usetrmnl/firmware). Technically we don't owe you an explanation to get up and running, but we'll provide one anyway. ;)

### Device setup

See our [BYOD guide](byod.md) for instructions to build a device that's compatible with our firmware.

### Server quickstart

The TRMNL web server generates PNG images. When a device pings our [Display API](../private-api/screens.md), the next-in-queue image is shared as an absolute URL inside a JSON response like this:

```
{
  "image_url"=>"https://trmnl.s3.us-east-2.amazonaws.com/path-to-img.png"
}
```

For several ready-made OSS server implementations, see [BYOS Implementations](https://docs.trmnl.com/go/diy/byos#implementations). To develop your own server that is TRMNL firmware compatible out of the box:

1. [build a device](byod.md)
2. change the base URL to your own server or local network from the WiFi Captive Portal
3. mimic the `api/setup` and `api/display` endpoints per our [firmware README](https://github.com/usetrmnl/firmware)
4. follow our [ImageMagick guide](imagemagick-guide.md) to create TRMNL firmware compatible images
5. profit

### Other infrastructure

In the quickstart above we glossed over a critical element: "next-in-queue" images.

At TRMNL we use a Playlists table to manage the ordering of plugin instances, letting users drag/drop different items in whatever sequence they prefer.

<figure><img src="../.gitbook/assets/trmnl-playlist-drag-drop.png" alt=""><figcaption><p>Drag/Drop Playlists UI</p></figcaption></figure>

Each item in a device's Playlist is an instance\* of a Plugin, something we call a PluginSetting.

This keeps our Plugins table immutable, for example Google Calendar is just a name, icon, and form field parameters. Meanwhile details about a _connection_ to Google Calendar are stored inside a PluginSetting record. Keep this in mind as you build your own server -- do you want to allow multiple connections to the same parent plugin?

TRMNL also offers a [Scheduler](https://app.gitbook.com/u/m0dkWlfTUdWGp1iNjs5aX2kHq1F3). This makes it easy to dictate conditions for when and why a given plugin is displayed on your device.

<figure><img src="../.gitbook/assets/TRMNL-playlist-scheduler.png" alt="Scheduler in action"><figcaption><p>Playlist scheduler in action</p></figcaption></figure>

Following our architecture is unnecessary for a self-hosted e-ink dashboard, but we do encourage you to check out those which have already been implemented in [BYOS clients](byos.md).
