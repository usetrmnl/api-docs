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

| Model | Resolution | Colors | Software | Setup |
| --- | --- | --- | --- | --- |
| Amazon Kindle 2024 `amazon_kindle_2024` | 1400x840 | 256 | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Amazon Kindle 7 `amazon_kindle_7` | 800x600 | 256 | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Amazon Kindle Oasis 2 `amazon_kindle_oasis_2` | 1680x1264 | 256 | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Amazon Kindle PW 6th Gen `amazon_kindle_paperwhite_6th_gen` | 1024x768 | 256 | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Amazon Kindle PW 7th Gen `amazon_kindle_paperwhite_7th_gen` | 1448x1072 | 256 | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Amazon Kindle PW Signature 11th Gen `amazon_kindle_paperwhite_signature_11th_gen` | 1648x1236 | 16 | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Amazon Kindle Scribe `amazon_kindle_scribe` | 2480x1860 | 256 | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Amazon Kindle Voyage `amazon_kindle_voyage` | 1448x1072 | 256 | [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (recommended) or [trmnl-kindle](https://github.com/usetrmnl/trmnl-kindle) | Jailbreak |
| Avalue EPD-42S 42" Display Board `avalue_epd_42s` | 2880x2160 | 16 | [See wizard](https://trmnl.com/byod) |  |
| Custom Device `byod_custom` | 800x480 | 2 | [TRMNL firmware](https://github.com/usetrmnl/trmnl-firmware) | Build and flash (see [Build from scratch](#build-from-scratch)) |
| ED133UT2 Active Matrix `ed133ut2` | 1600x1200 | 16 | [See wizard](https://trmnl.com/byod) |  |
| Generic 16:9 Display `generic_16_9` | 1920x1080 | 256 | [See wizard](https://trmnl.com/byod) |  |
| Inkplate 10 `inkplate_10` | 1200x825 | 4 | [HomePlate](https://github.com/lanrat/homeplate) (community) | Flash |
| Inkplate 13 Spectra `inkplate_13_spectra` | 1600x1200 | 2 | [HomePlate](https://github.com/lanrat/homeplate) (community) | Flash |
| Inkplate 5.2 `inkplate_5_2` | 1280x720 | 4 | [HomePlate](https://github.com/lanrat/homeplate) (community) | Flash |
| Inkplate 6 Plus `inkplate_6_plus` | 1024x758 | 4 | [HomePlate](https://github.com/lanrat/homeplate) (community) | Flash |
| Inkplate 6COLOR `inkplate_6_color` | 600x448 | 2 | [HomePlate](https://github.com/lanrat/homeplate) (community) | Flash |
| Inky Impression 13.3 `inky_impression_13_3` | 1600x1200 | 2 | [trmnl-display](https://github.com/usetrmnl/trmnl-display) | Install script |
| Inky Impression 7.3 `inky_impression_7_3` | 800x480 | 2 | [trmnl-display](https://github.com/usetrmnl/trmnl-display) | Install script |
| Joan 13 `joan_13` | 1600x1200 | 16 | [See wizard](https://trmnl.com/byod) |  |
| Kobo Aura H2O Edition 2 `kobo_aura_h2o_2` | 1430x1080 | 16 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Aura HD `kobo_aura_hd` | 1440x1080 | 16 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Aura One `kobo_aura_one` | 1872x1404 | 256 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Clara 2E `kobo_clara_2e` | 1072x1448 | 16 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Forma `kobo_forma` | 1920x1440 | 16 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Glo `kobo_glo` | 1024x768 | 16 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Libra 2 `kobo_libra_2` | 1680x1264 | 256 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Libra Color `kobo_libra_color` | 1680x1264 | 4,096 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Sage `kobo_sage` | 1920x1440 | 16 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| Kobo Touch `kobo_touch` | 800x600 | 16 | [trmnl-kobo](https://github.com/usetrmnl/trmnl-kobo) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) | NickelMenu |
| M5PaperS3 `m5_paper_s3` | 960x540 | 16 | [See wizard](https://trmnl.com/byod) |  |
| Meta Portal `meta_portal` | 1280x800 | 16,777,216 | [See wizard](https://trmnl.com/byod) |  |
| Nook Simple Touch `nook_simple_touch` | 800x600 | 256 | [trmnl-nook-simple-touch](https://github.com/usetrmnl/trmnl-nook-simple-touch) | Root |
| Onyx BOOX Go 10.3 (Gen II) Lumi `onyx_boox_go_10_3_lumi` | 2480x1860 | 256 | [TRMNL Display](https://play.google.com/store/apps/details?id=ink.trmnl.android) ([source](https://github.com/usetrmnl/trmnl-android)) | App install |
| Onyx BOOX Go 7 `onyx_boox_go_7` | 1680x1264 | 16 | [TRMNL Display](https://play.google.com/store/apps/details?id=ink.trmnl.android) ([source](https://github.com/usetrmnl/trmnl-android)) | App install |
| Onyx BOOX Nova Air C `onxy_boox_nova_air_c` | 1872x1404 | 4,096 | [TRMNL Display](https://play.google.com/store/apps/details?id=ink.trmnl.android) ([source](https://github.com/usetrmnl/trmnl-android)) | App install |
| Onyx BOOX Palma `palma` | 1648x824 | 256 | [TRMNL Display](https://play.google.com/store/apps/details?id=ink.trmnl.android) ([source](https://github.com/usetrmnl/trmnl-android)) | App install |
| Onyx BOOX Poke 5 `onyx_boox_poke_5` | 1072x1448 | 16 | [TRMNL Display](https://play.google.com/store/apps/details?id=ink.trmnl.android) ([source](https://github.com/usetrmnl/trmnl-android)) | App install |
| OpenPeak OpenFrame `openframe` | 800x480 | 16,777,216 | [See wizard](https://trmnl.com/byod) |  |
| Playdate `playdate` | 400x240 | 2 | [trmnl-playdate](https://github.com/usetrmnl/trmnl-playdate) | Sideload |
| Raspberry Pi Touch 2 `raspberry_pi_touch_2` | 1280x720 | 16,777,216 | [trmnl-display](https://github.com/usetrmnl/trmnl-display) | Install script |
| reMarkable 2 `remarkable_paper_2` | 1404x1872 | 16 | [trmnl-remarkable](https://github.com/usetrmnl/trmnl-remarkable) (Paper Pro) or [KOReader plugin](https://github.com/usetrmnl/trmnl-koreader) (reMarkable 2) | Developer Mode |
| Seeed E1001 Monochrome `seeed_e1001` | 800x480 | 4 | TRMNL firmware | [Flash from your browser](https://trmnl.com/flash) |
| Seeed E1002 `seeed_e1002` | 800x480 | 6 | TRMNL firmware | [Flash from your browser](https://trmnl.com/flash) |
| Seeed E1003 (4-bit) `seeed_e1003` | 1872x1404 | 16 | TRMNL firmware | [Flash from your browser](https://trmnl.com/flash) |
| Seeed E1004 `seeed_e1004` | 1600x1200 | 16 | [See wizard](https://trmnl.com/byod) |  |
| Seeed Sticky `seeed_sticky` | 800x480 | 4 | TRMNL firmware | [Flash from your browser](https://trmnl.com/flash) |
| TCL NxtPaper 14 `tcl_nxtpaper_14` | 2400x1600 | 16,777,216 | [See wizard](https://trmnl.com/byod) |  |
| Tidbyt `tidbyt` | 64x32 | 16,777,216 | [See wizard](https://trmnl.com/byod) |  |
| Vestaboard `vestaboard` | 22x6 | 16,777,216 | [See wizard](https://trmnl.com/byod) |  |
| Waveshare 4.26" (2-bit) `waveshare_4_26` | 800x480 | 4 | [TRMNL firmware](https://github.com/usetrmnl/trmnl-firmware) | Build and flash (see [Build from scratch](#build-from-scratch)) |
| Waveshare 5.83" (Steam Machine) `waveshare_5_8_bw` | 648x480 | 4 | [TRMNL firmware](https://github.com/usetrmnl/trmnl-firmware) | Build and flash (see [Build from scratch](#build-from-scratch)) |
| Waveshare 7.5" B/W `waveshare_7_5_bw` | 800x480 | 2 | [TRMNL firmware](https://github.com/usetrmnl/trmnl-firmware) | Build and flash (see [Build from scratch](#build-from-scratch)) |
| Waveshare 7.5" B/W/R `waveshare_7_5_bwr` | 800x480 | 2 | [TRMNL firmware](https://github.com/usetrmnl/trmnl-firmware) | Build and flash (see [Build from scratch](#build-from-scratch)) |
| Waveshare 7.5" B/W/R/Y `waveshare_7_5_bwry` | 800x480 | 2 | [TRMNL firmware](https://github.com/usetrmnl/trmnl-firmware) | Build and flash (see [Build from scratch](#build-from-scratch)) |
| Xteink X3 `xteink_x3` | 792x528 | 4 | TRMNL firmware | [Flash from your browser](https://trmnl.com/flash) |
| Xteink X4 `xteink_x4` | 800x480 | 4 | TRMNL firmware | [Flash from your browser](https://trmnl.com/flash) |

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
