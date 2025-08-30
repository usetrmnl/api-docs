---
description: Overview of TRMNL's architecture.
---

# How it Works

<figure><img src=".gitbook/assets/TRMNL architecture overview.png" alt=""><figcaption><p>Device, Server, Native Plugins, 3rd Party Developer, Firmware Components</p></figcaption></figure>

The TRMNL **web server** hosts a growing directory of [first-party plugins](https://usetrmnl.com/integrations) and [community plugins](https://usetrmnl.com/recipes) that are driven by [API endpoints](https://usetrmnl.com/api-docs) + a [templating engine](https://help.usetrmnl.com/en/articles/10671186-liquid-101). Our [Framework UI](https://usetrmnl.com/framework) design system is recommended, but not required, for plugin development. Learn how to build custom plugins [here](https://help.usetrmnl.com/en/articles/9510536-custom-plugins).

The TRMNL **device** is a custom PCB featuring an ESP32-C3 microcontroller, 1800-2500 mAh battery, and 7.5" EPD screen housed in injection-molded ABS soft touch plastic. Customers may disassemble their device, mod their firmware, and retrieve their API keys without impacting our [Terms of Service](https://usetrmnl.com/terms).

TRMNL **firmware** supports automatic OTA (over the air) updates to WiFi-connected devices and is [open source](https://github.com/usetrmnl/firmware). Here's how it works:

1. TRMNL device wakes up and requests content from web server every _n_ period\*
2. TRMNL web server generates a 1- or 2-bit PNG image. Response JSON includes a link to this image and timing instructions for the next "refresh" request.
3. TRMNL device renders the content, then goes to sleep for the instructed amount of time.

{% hint style="info" %}
\* "Displayable content" is the most recently created screen, in order of priority according to the [Playlists](https://help.usetrmnl.com/en/articles/11663305-playlist-scheduler) interface. "N" is a value in minutes, configurable by customers at a per-plugin or per-device level.
{% endhint %}

## Opinionated device <> server relationship

Most IoT products support SSH-ing directly into peripheral devices. We've heard too many horror stories about how this can go wrong, and decided to invert the paradigm.

**Your TRMNL device pings our server, never the other way around**.

Each request to our `/api/display` endpoint ([docs](https://docs.usetrmnl.com/go/private-api/screens)) includes only the minimum details needed to support customers -- an API key, device mac address, firmware version, battery voltage, and WiFi signal strength.

**We do not collect any footprint of your location or identity**, such as IP address or WiFi credentials. Your local network's SSID and password are stored only on your TRMNL device.

When the TRMNL web server responds to a device's request we include only a few fields. These include "update\_firmware" (true/false), a direct download link to the firmware's \[public] binary package, and whether the device should be reset. Customers may disable OTA updates, reset their device to transfer ownership, or destroy data from their web account.

**TRMNL does not store rendered content over time.**

Whenever the web server generates a new image, it replaces the previous image. This [keeps our costs low](https://x.com/useTRMNL/status/1892058143636476374), affording perpetual service without subscription fees. This also protects users, because we only have access to the most recent screen rendered for each of your plugins.
