---
description: Bring your own device to TRMNL.
---

# BYOD

Before diving into "how," it's worth mentioning that **the investment required to build your own device could be greater than our retail price**.&#x20;

Making your own TRMNL from scratch is not an economically rational decision, but rather a labor of love. We learned this the ~~hard~~ fun way while building v1 over 7 months, from Dec 2023 to July 2024.

Here's what you can expect to spend per component:

* Battery, $5 (unnecessary if you prefer plugged in)
* EPD screen, $50 ([this one](https://amazon.com/dp/B075R69T93/) is compatible)
* Microcontroller, $3-30 (depends if you build/solder yourself or leverage a PCB prototyper)
* Enclosure/case, $3-20 (print [one of ours](https://github.com/usetrmnl/mounts) or design your own)

If you know what you're doing and just need some firmware or a server client, here ya go:

* Firmware: [https://github.com/usetrmnl/firmware](https://github.com/usetrmnl/firmware)
* Server (multiple options): [https://docs.usetrmnl.com/go/diy/byos](https://docs.usetrmnl.com/go/diy/byos)

### Quickstart

When you're ready to DIY a TRMNL:

1. Buy access to the TRMNL web app + API: [https://shop.usetrmnl.com/products/byod](https://shop.usetrmnl.com/products/byod)
2. Create a BYOD device: [https://usetrmnl.com/claim-a-device](https://usetrmnl.com/claim-a-device)
3. Visit your [device settings page](https://usetrmnl.com/devices/current/edit) to select your [Device Model](https://help.usetrmnl.com/en/articles/11547008-device-model-faq) and set your DIY device's MAC address
4. Flash [our firmware](https://github.com/usetrmnl/firmware) to your DIY device + follow steps to pair WiFi. These steps are different pending the guide you're using (Kindle, Kobo, Android, etc)
5. Your DIY device will render a 6-digit ID; this is your device's Friendly ID and is already visible inside your Device settings. No action is required.
6. Connect native apps or start building private plugins from the Plugins tab
7. Stay focused

If you have questions, send us a live chat or join the Developer-only Discord, accessible from your [Account](https://usetrmnl.com/account) tab.

### DIY Kit

(_Coming July 2, 2025 - tune into the live stream below_)

{% embed url="https://www.youtube.com/watch?v=MZ8HMSGqBWI" %}
TRMNL + Seeed Studio partnership launch
{% endembed %}

If you're a Seeed Studio early adopter, check out this helpful guide from a mutual customer. You can also  leverage the [Seeed Wiki guide to TRMNL](https://wiki.seeedstudio.com/xiao_7_5_inch_epaper_panel_with_trmnl/).

{% embed url="https://www.youtube.com/watch?v=QAGTRrbQSBE" %}

