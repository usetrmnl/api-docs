---
description: Buy a TRMNL device, then point it at your own server.
---

# BYOS (Build Your Own Server)

### Why

TRMNL intends to ensure that **every device is un-brickable and can run with zero external dependencies**. BYOS is one aspect of making this possible for you.

### Quick Start

1. Purchase a TRMNL from our [store](https://trmnl.com).
2. Choose a BYOS implementation for your stack (see below). Our flagship implementation is [Terminus](https://github.com/usetrmnl/terminus), so we recommend you get started there.

### Audience

This page is primarily for BYOS maintainers but might also be helpful for anyone wanting to get a high level overview of what each implementation can do before spinning up on your own network.

### Implementations

We support multiple implementations developed by us and the community at large. The goal isn't for BYOS to match parity with our hosted solution but to provide enough of a pleasant solution for your own customized experience. There are trade offs either way but we've got you covered for whatever path you wish to travel.

**Legend**

Use this legend to understand the matrix of features below.

* 🟢 Supported.
* 🟡 Partially supported.
* 🔴 Not supported or not implemented.
* ⚪️ Unknown.

**Matrix**

Below is a list of all implementations in various languages/frameworks you can use to self-host and manage your devices with:

<table><thead><tr><th width="150.58984375">Implementation</th><th>Stack</th><th width="121.6953125">Dashboard</th><th width="172.37109375">Auto-Provisioning</th><th width="111.859375">Devices</th><th>JSON Data API</th><th>Image Previews</th><th>Playlists</th><th>Plugins</th><th>Recipes</th><th>Sensors</th><th>Docker</th><th>Test Suite</th><th>Maintained</th><th>Semantic Versioning</th></tr></thead><tbody><tr><td><a href="https://github.com/usetrmnl/terminus"><strong>Terminus</strong></a></td><td>Ruby/Hanami</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td></tr><tr><td><a href="https://github.com/usetrmnl/larapaper"><strong>LaraPaper</strong></a></td><td>PHP/Laravel</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td></tr><tr><td><a href="https://github.com/usetrmnl/inker"><strong>Inker</strong></a></td><td>JavaScript</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>⚪️</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_next"><strong>BYOS Next.js</strong></a></td><td>JavaScript/Next.js</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🟢</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_fastapi"><strong>BYOS Fast API</strong></a></td><td>Python/FastAPI</td><td>🟢</td><td>⚪️</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>⚪️</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>⚪️</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_django"><strong>BYOS Django</strong></a></td><td>Python/Django</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🔴</td><td>🔴</td><td>⚪️</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_phoenix"><strong>BYOS Phoenix</strong></a></td><td>Elixir/Phoenix</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>⚪️</td></tr></tbody></table>

The following provides a detailed breakdown of each of the above features:

* **Dashboard**: Provides a high level overview of information mostly in terms of quick links, statistics, charts, graphs, system health, etc.
* **Auto-Provisioning**: Devices can be automatically provisioned once added to your network. This includes the automatic provisioning of new and existing devices.
* **Devices**: Provides device management in terms of updating each device, viewing current image, viewing logs, and more.
* **JSON Data API**: Provides full API support using a JSON Data API for device management, image generation, logging, and more.
* **Image Previews**: Provides a UI for quickly, and dynamically, generating new device screens.
* **Playlists**: Supports playlist configuration and management in terms of timing, order, and display of screens on devices. This can also include proxying to our Core server.
* **Plugins**: Supports installation and hosting of custom plugins. This can also include proxying to our Core server.
* **Recipes**: Supports installation and hosting of custom plugins. This can also include proxying to our Core server.
* **Sensors**: Supports sensors connected via [Qwiic Cables](https://www.sparkfun.com/flexible-qwiic-cable-50mm.html) either to the server (via Raspberry Pi) or via a TRMNL compatible device. Please see the [TRMNL Sensor Scanner](https://github.com/usetrmnl/sensor_scanner) project for further details.
* **Docker**: Supports Docker for both local development and production deployment.
* **Test Suite**: Has a test suite with near 100% test coverage, is fully runnable locally, and is wired up with automatic Continuous Integration (CI) builds.
* **Maintained**: Project is maintained and kept up-to-date on a weekly (or monthly) basis in terms of dependencies, firmware updates, and keeping up-to-date with any/all Core changes.
* **Semantic Versioning**: Supports [strict semantic versioning](https://alchemists.io/articles/strict_semantic_versioning).

### API

At a minimum, the following API endpoints should be supported for all BYOS implementations. The headers below are the ones our firmware sends.

#### Setup

The device calls this once, after WiFi setup, to trade its MAC address for an API key.

```shell
curl "http://byos.local/api/setup" \
    -H 'ID: <device_mac_address>' \
    -H 'FW-Version: 1.8.16' \
    -H 'Model: og' \
    -H 'Content-Type: application/json'
```

The firmware reads `status`, `api_key`, `friendly_id`, `image_url` + `message`, and stores `api_key` for every request after this one. Any `status` other than `200` counts as a failed setup.

Example response:

```json
{
  "status": 200,
  "api_key": "<device_api_key>",
  "friendly_id": "ABC123",
  "image_url": "http://byos.local/images/setup-logo.bmp",
  "message": "Register at byos.local with Device ID 'ABC123'"
}
```

#### Display

The device calls this on every wake. It also sends battery, WiFi + screen details as headers (`Battery-Voltage`, `RSSI`, `Width`, `Height`, `Refresh-Rate` and more); see [Screens](../private-api/screens.md) for the full list.

```bash
curl "http://byos.local/api/display" \
     -H 'ID: <device_mac_address>' \
     -H 'Access-Token: <device_api_key>' \
     -H 'FW-Version: 1.8.16' \
     -H 'Content-Type: application/json'
```

Example response:

```json
{
  "status": 0,
  "image_url": "http://byos.local/images/screen-3f2a9c-1781785364.png",
  "filename": "screen-3f2a9c-1781785364",
  "refresh_rate": 900,
  "reset_firmware": false,
  "update_firmware": false,
  "firmware_url": null,
  "special_function": "identify",
  "maximum_compatibility": false,
  "temperature_profile": "default"
}
```

The firmware reads these fields:

* `status` -- `0` draws `image_url`; `202` means "not registered yet" and the device polls again in a few seconds
* `image_url` + `filename` -- see [Filenames](#filenames)
* `refresh_rate` -- seconds to sleep before the next request. Send a number (`900`), not a string (`"900"`); the firmware reads a string as `0` and wakes again at once
* `reset_firmware` -- `true` makes the device erase its WiFi credentials + API key
* `update_firmware` + `firmware_url` -- `true` + a `.bin` URL triggers an OTA update. Firmware builds are per model, so only send a TRMNL X build to a TRMNL X
* `special_function` -- what a button press does: `none`, `identify`, `sleep`, `add_wifi`, `restart_playlist`, `rewind`, `send_to_me` or `guest_mode`. This is a setting, so send the same value on every response
* `maximum_compatibility` -- `true` fixes display issues on some ePaper driver chips but turns off fast refresh. Optional, defaults to `false`
* `temperature_profile` -- `default`, `a` or `b`. Leave it at `default` unless images look washed out

Our hosted server also sends `touchbar_mode` to a TRMNL X. Current firmware ignores it, so you can leave it out.

#### Filenames

The device saves each new image to flash under its `filename`. When a response names a file it already has, it shows that copy and downloads nothing. So:

* Change `filename` only when the image changes, never on every request. A new name on every request downloads + writes the image on every wake.
* Use the format `<name>-<id>-<unix time>`, e.g. `screen-3f2a9c-1781785364`. `<name>-<id>` (13 characters) names the screen and never changes; the time is when this image was made. Each time the device saves a new image, it deletes older images of the same screen, and every saved image that does not end in a 10-digit timestamp or is more than 24 hours old.
* Keep it to 31 characters or less. The device shortens a longer name to its first 7 + last 17 characters, so two long names can collide and the second image never shows.

#### Images

Render each image at the size the device sends in its `Width` + `Height` headers, and serve it with the right `Content-Type`. The firmware picks the decoder from that header, not from the URL: `image/png` for PNG, `image/jpeg` for JPEG. It reads any other response as a BMP.

| Model (`Model` header) | Size | Grays | Formats | Largest file |
| --- | --- | --- | --- | --- |
| TRMNL OG (`og`) | 800x480 | 2 or 4 | PNG, JPEG, 1-bit BMP | 90,000 bytes |
| TRMNL X (`x`) | 1872x1404 | 16 | PNG, JPEG | 750,000 bytes |

A BMP must be exactly 800x480 at 1 bit per pixel.

#### Logs

When something goes wrong (a failed download, a bad image), the device posts its logs here:

```bash
curl -X POST "http://byos.local/api/log" \
     -H 'ID: <device_mac_address>' \
     -H 'Access-Token: <device_api_key>' \
     -H 'Content-Type: application/json' \
     -d '{"logs": [{"message": "..."}]}'
```

💡 For a detailed breakdown of all API endpoints and what they can do, please refer to the [Terminus API Documentation](https://github.com/usetrmnl/terminus?tab=readme-ov-file#api) or the [TRMNL API](https://github.com/usetrmnl/trmnl-api) gem which provides a Ruby API client for talking to our servers.

### Securing With HTTPS

Most BYOS implementations serve up content over plain HTTP. If you prefer TLS connections, you can put a reverse proxy in front of the server. Caddy is a popular option. You can use self-signed certificates, or real ones from Let's Encrypt. See [this community issue](https://github.com/usetrmnl/trmnl-firmware/issues/58#issue-2826999580) for details on how to set it up yourself.
