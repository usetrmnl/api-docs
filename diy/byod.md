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

1. Build a device and [flash our firmware](https://github.com/usetrmnl/trmnl-firmware) -- or flash it from your browser at [trmnl.com/flash](https://trmnl.com/flash)
2. Spin up a [BYOS server client](https://docs.trmnl.com/go/diy/byos#implementations)

**OSS + closed source approach**

1. Build a device and [flash our firmware](https://github.com/usetrmnl/trmnl-firmware) -- or flash it from your browser at [trmnl.com/flash](https://trmnl.com/flash)
2. [Buy a BYOD license](https://shop.trmnl.com/products/byod) (one-time) to the TRMNL web app + API, or start a [14-day free trial](https://trmnl.com/byod-trial)
3. Create a BYOD device: [https://trmnl.com/claim-a-device](https://trmnl.com/claim-a-device) (trial accounts get one automatically)
4. Visit your [device settings page](https://trmnl.com/devices/current/edit) to select your [Device Model](https://help.trmnl.com/en/articles/11547008-device-models) and then, under the [Developer Perks](https://trmnl.com/devices/current/developer/edit) section set your DIY device's MAC address
5. Your DIY device will render a 6-character ID; this is your device's Friendly ID and is already visible inside your Device settings. No action is required.
6. Connect native apps or **start building private plugins** from the Plugins tab; this is equivalent access as "Developer Edition" for TRMNL hardware.

{% hint style="info" %}
Our server matches your device by the MAC address it sends in the `ID` header of `/api/setup`. If setup answers "MAC not registered," double check step 4.
{% endhint %}

### Other screens

Kindle, Kobo, Nook, BOOX, Raspberry Pi, iPad + Android tablets can run TRMNL too -- some with a companion app, others with a jailbreak. Pick your hardware in the wizard at [trmnl.com/byod](https://trmnl.com/byod) for step-by-step instructions, and browse the supported [device models](https://trmnl.com/api/models).

### DIY Kit (Intermediate)

On July 17, 2025 we announced a partnership with Seeed Studio.

* [Get the DIY kit](https://www.seeedstudio.com/TRMNL-7-5-Inch-OG-DIY-Kit-p-6481.html)
* [Flash the firmware](https://trmnl.com/flash) from your browser (the Seeed OG DIY Kit, XIAO 7.5" panel, E1001 + E1002 are all listed)
* [Get a BYOD license](https://shop.trmnl.com/products/byod) (optional)
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

Send us a live chat or join the Developer-only Discord, accessible from your [Account](https://trmnl.com/account) tab.
