---
description: Bring your own device to TRMNL.
---

# BYOD

BYOD means your hardware, our server. Build a device from scratch, or give an old e-reader, tablet or Raspberry Pi a second life, and run it on the TRMNL web app and plugins.

Not sure your hardware fits? Pick it in the wizard at [trmnl.com/byod](https://trmnl.com/byod) to see setup steps and builds from other people.

### How it works

1. [Buy a BYOD license](https://shop.trmnl.com/products/byod) (one-time, one per device) or start a [14-day free trial](https://trmnl.com/byod-trial)
2. Create a BYOD device: [https://trmnl.com/claim-a-device](https://trmnl.com/claim-a-device) (trial accounts get one automatically)
3. Visit your [device settings page](https://trmnl.com/devices/current/edit) to select your [Device Model](https://help.trmnl.com/en/articles/11547008-device-models) and then, under the [Developer Perks](https://trmnl.com/devices/current/developer/edit) section set your device's MAC address
4. Connect your hardware (see [Supported hardware](#supported-hardware)):
   * **TRMNL firmware** (ESP32 boards) needs nothing else. The device sends its MAC address to our server and receives its API key.
   * **Client apps** (e-readers, Linux, Android) need the Device API Key from [Developer Perks](https://trmnl.com/devices/current/developer/edit) pasted into their settings.
5. Connect native apps or **start building private plugins** from the Plugins tab; this is equivalent access as "Developer Edition" for TRMNL hardware.

{% hint style="info" %}
Our server matches your device by the MAC address it sends in the `ID` header of `/api/setup`. If setup answers "MAC not registered," double check step 3.
{% endhint %}

Mirroring a TRMNL you already own, for example on an iPad, needs no license.

### Supported hardware

| Hardware | Software | Setup |
| --- | --- | --- |
| Seeed Studio OG DIY Kit, XIAO 7.5" panel, reTerminal E1001 / E1002 / E1003 | TRMNL firmware | [Flash from your browser](https://trmnl.com/flash) |
| Xteink X4 | TRMNL firmware | [Flash from your browser](https://trmnl.com/flash) |
| Other ESP32 boards + ePaper panels | [TRMNL firmware](https://github.com/usetrmnl/trmnl-firmware) | Build and flash (see [Build from scratch](#build-from-scratch)) |
| Kindle | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Kobo | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| reMarkable | [trmnl-remarkable](https://github.com/usetrmnl/trmnl-remarkable) (Paper Pro) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (reMarkable 2) | Developer Mode |
| Nook GlowLight 4 | [trmnl-nook](https://github.com/usetrmnl/trmnl-nook) | ADB sideload |
| Nook Simple Touch | [trmnl-nook-simple-touch](https://github.com/usetrmnl/trmnl-nook-simple-touch) | Root |
| BOOX and other Android devices | [TRMNL Display](https://play.google.com/store/apps/details?id=ink.trmnl.android) ([source](https://github.com/usetrmnl/trmnl-android)) | App install |
| Raspberry Pi / Linux SBC (HDMI, Waveshare HATs, Pimoroni Inky Impression) | [trmnl-display](https://github.com/usetrmnl/trmnl-display) | Install script |
| Inkplate | [HomePlate](https://github.com/lanrat/homeplate) (community) | Flash |
| Playdate | [trmnl-playdate](https://github.com/usetrmnl/trmnl-playdate) | Sideload |
| iPad | [trmnl.com/mirror](https://trmnl.com/mirror) mirrors a TRMNL you own, no license needed. A native iPad mode in the TRMNL Companion app is coming soon. | Open in Safari |

Exact resolutions and color palettes for every device model are at [trmnl.com/api/models](https://trmnl.com/api/models).

### Build from scratch

Before diving into "how," it's worth mentioning **the investment required to build your own device could be greater than our retail price**.

Making a TRMNL from scratch is not an economically rational decision, but rather a labor of love. We learned this the ~~hard~~ fun way between December 2023 and July 2024.

Here's what you can expect to spend per component:

* Battery, $5 (unnecessary if you prefer plugged in)
* EPD screen, $50 ([this one](https://amazon.com/dp/B075R69T93/) is compatible)
* Microcontroller, $3-30 (build yourself or leverage a PCB prototyper)
* Enclosure/case, $3-20 (print [one of ours](https://github.com/usetrmnl/mounts) or design your own)

Then [flash our firmware](https://github.com/usetrmnl/trmnl-firmware) -- or flash it from your browser at [trmnl.com/flash](https://trmnl.com/flash) -- and either follow [How it works](#how-it-works) above, or skip the license and spin up a [BYOS server client](https://docs.trmnl.com/go/diy/byos#implementations).

### Seeed Studio

On July 17, 2025 we announced a partnership with Seeed Studio.

* [Get the DIY kit](https://www.seeedstudio.com/TRMNL-7-5-Inch-OG-DIY-Kit-p-6481.html)
* [Flash the firmware](https://trmnl.com/flash) from your browser (the Seeed OG DIY Kit, XIAO 7.5" panel, E1001, E1002 + E1003 are all listed)
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
