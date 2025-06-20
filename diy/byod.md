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

When you're ready to start building:

1. Buy access to the TRMNL web app + API: [https://shop.usetrmnl.com/products/byod](https://shop.usetrmnl.com/products/byod)
2. Create a (temporary) virtual device: [https://usetrmnl.com/claim-a-device](https://usetrmnl.com/claim-a-device)
3. Register your DIY device's MAC ([find it](https://help.usetrmnl.com/en/articles/10614205-finding-your-trmnl-mac-address)): [https://usetrmnl.com/devices](https://usetrmnl.com/devices) (click yours to edit)
4. Flash our firmware to your DIY device: [easy](https://usetrmnl.com/flash), [advanced](https://help.usetrmnl.com/en/articles/10271569-manually-flash-firmware)
5. Set up your DIY device by turning it on + following the steps to pair WiFi
6. Your DIY device will produce a 6-digit ID; input this inside your existing TRMNL account, via the top-right dropdown > add new device. This will replace your temporary virtual device from Step 2
7. Connect native apps or start building private plugins from the Plugins tab
8. Stay focused

Email team@usetrmnl.com if you have any questions, or join the Developer-only Discord, accessible from your Account tab.

### DIY Kit

(_Coming at the end of June, 2025_)

If you're a Seeed Studio early adopter, check out this helpful guide from a mutual customer. You can also  leverage the [Seeed Wiki guide to TRMNL](https://wiki.seeedstudio.com/xiao_7_5_inch_epaper_panel_with_trmnl/).

{% embed url="https://www.youtube.com/watch?v=QAGTRrbQSBE" %}

