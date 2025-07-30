---
description: Bring your own device to TRMNL.
---

# BYOD

Before diving into "how," it's worth mentioning **the investment required to build your own device could be greater than our retail price**.

Making a TRMNL from scratch is not an economically rational decision, but rather a labor of love. We learned this the ~~hard~~ fun way between December 2023 and July 2024.

Here's what you can expect to spend per component:

* Battery, $5 (unnecessary if you prefer plugged in)
* EPD screen, $50 ([this one](https://amazon.com/dp/B075R69T93/) is compatible)
* Microcontroller, $3-30 (build yourself or leverage a PCB prototyper)
* Enclosure/case, $3-20 (print [one of ours](https://github.com/usetrmnl/mounts) or design your own)

### Build from scratch (Advanced)

**OSS approach**

1. Build a device and [flash our firmware](https://github.com/usetrmnl/trmnl-firmware)
2. Spin up a [BYOS server client](https://docs.usetrmnl.com/go/diy/byos#implementations)

**OSS + closed source approach**

1. Build a device and [flash our firmware](https://github.com/usetrmnl/trmnl-firmware)
2. [Buy access](https://shop.usetrmnl.com/products/byod) to the TRMNL web app + API
3. Create a BYOD device: [https://usetrmnl.com/claim-a-device](https://usetrmnl.com/claim-a-device)
4. Visit your [device settings page](https://usetrmnl.com/devices/current/edit) to select your [Device Model](https://help.usetrmnl.com/en/articles/11547008-device-model-faq) and set your DIY device's MAC address
5. Your DIY device will render a 6-digit ID; this is your device's Friendly ID and is already visible inside your Device settings. No action is required.
6. Connect native apps or start building private plugins from the Plugins tab

### DIY Kit (Intermediate)

On July 17, 2025 we announced a partnership with Seeed Studio.&#x20;

* [Get the DIY kit](https://www.seeedstudio.com/TRMNL-7-5-Inch-OG-DIY-Kit-p-6481.html)
* [Get a BYOD license](https://shop.usetrmnl.com/products/byod) (optional)
* [Seeed Wiki - XIAO 7.5" panel](https://wiki.seeedstudio.com/xiao_7_5_inch_epaper_panel_with_trmnl/) (May 2025)
* [Seeed Wiki - TRMNL DIY Kit](https://wiki.seeedstudio.com/trmnl_7inch5_diy_kit_main_page/) (July 2025)

{% embed url="https://www.youtube.com/watch?v=MZ8HMSGqBWI" %}
TRMNL + Seeed Studio partnership launch
{% endembed %}

If you're a Seeed Studio early adopter (XIAO esp32-c3 board), check out the community guides below for in-depth setup assistance. You can also leverage the [Seeed Wiki guide to TRMNL](https://wiki.seeedstudio.com/xiao_7_5_inch_epaper_panel_with_trmnl/).

{% embed url="https://www.youtube.com/watch?v=Tr__8OlQQms" %}
E-Paper Dashboard without coding | Xiao E-Paper Display and TRMNL Firmware
{% endembed %}

{% embed url="https://www.youtube.com/watch?v=QAGTRrbQSBE" %}
Seeed Studio XIAO Esp32-C3 board
{% endembed %}

### Need Help?

Send us a live chat or join the Developer-only Discord, accessible from your [Account](https://usetrmnl.com/account) tab.
