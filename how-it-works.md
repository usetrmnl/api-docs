---
description: Overview of the TRMNL architecture.
---

# How it Works

<figure><img src=".gitbook/assets/TRMNL architecture overview.png" alt=""><figcaption><p>Device, Server, Native Plugins, 3rd Party Developer, Firmware Components</p></figcaption></figure>

The TRMNL **web server** hosts a growing directory of [native plugins](https://usetrmnl.com/integrations) and API endpoints + templating engine for **custom plugins**, managed directly by customers. Learn to build a custom plugin [here](https://help.usetrmnl.com/en/articles/9510536-custom-plugins).

The TRMNL **device** is a custom PCB featuring an ESP32-C3 microcontroller, 1800-2500 mAh battery, and 7.5" EPD screen housed in injection-molded ABS soft touch plastic. Customers may disassemble their device, mod their firmware, and retrieve their API keys (_or pay a small one-time fee to unlock the Developer add-on_) without impacting our [Terms of Service](https://usetrmnl.com/terms).

TRMNL **firmware** supports automatic OTA (over the air) updates to WiFi-connected devices and is [open source](https://github.com/usetrmnl/firmware). Here's how it works:

1. TRMNL device wakes up and sends request to web server for displayable content every _n_ period\*
2. TRMNL web server generates a single-use, 1-bit, bitmap image (800x480 pixels). Response JSON includes a link to this image and timing instructions for the next "refresh" request.
3. TRMNL device renders the content, then goes to sleep for the instructed amount of time.

{% hint style="info" %}
\* "Displayable content" is the most recently created screen, in order of priority according to the [Playlists](https://usetrmnl.com/playlists) interface. "N" is a value in minutes, configurable by customers from the [Devices > Edit](https://usetrmnl.com/devices/) web interface.&#x20;
{% endhint %}

## Opinionated device <> server relationship

Most IoT products support SSH-ing directly into peripheral devices. We've heard too many horror stories about how this can go wrong, and decided to invert the paradigm.

**Your TRMNL device pings our server, never the other way around**.

Each request made to our `/api/display` endpoint includes only the minimum details needed to support customers -- an API key, device mac address, firmware version, battery voltage, and wifi signal strength.

**We do not collect any footprint of your location or identity**, such as IP address or WiFi configuration. The SSID and password for your local network are stored only on your TRMNL device.

When the TRMNL web server responds to a device's request we include only a few fields. These include "update\_firmware" (true/false), a direct download link to the firmware's \[public] binary package, and whether the device should be reset. Customers may reset their device to transfer ownership or safely destroy data from their web account.

**TRMNL does not store rendered content over time.**

Whenever the web server generates a new bitmap image, it replaces the previous image. This keeps our costs low, allowing us to provide perpetual service without subscription fees. This also protects users, because we only have access to the most recent screen rendered for each of your plugins.
