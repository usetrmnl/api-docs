---
description: Buy a TRMNL device, then point it at your own server.
---

# BYOS

First, purchase a TRMNL from our [home page](https://usetrmnl.com). Then choose a BYOS implementation for your stack. Our reference implementation is Terminus (Hanami) and we recommended you get started there but you can also choose from other languages/frameworks as well.

**Screencast**

The following screencast will walk you through setting up Terminus and connecting your device to it.

{% embed url="https://youtu.be/Z_XS7py05fA?si=hROpfIUw-kkJiEOV" %}

**Why BYOS?**

TRMNL intends to ensure that **every device is un-brickable and can run with zero external dependencies**.

### Implementations

We support multiple implementations developed by us and the community at large. The goal isn't for BYOS to match parity with our hosted solution but to provide enough of a pleasant solution for your own customized experience. There are trade offs either way but we've got you covered for whatever path you wish to travel.

**Legend**

Use this legend to understand the matrix of features below.

* 🟢 Supported.
* 🟡 Partially supported.
* 🔴 Not supported or not implemented.
* ⚫️ Archived with minimal maintenance support.
* ⚪️ Unknown.

**Matrix**

Below is a list of all implementations in various languages/frameworks you can use to self-host and manage your devices with:

<table><thead><tr><th>Implementation</th><th width="128">Dashboard</th><th>Auto-Provisioning</th><th>Devices</th><th>JSON Data API</th><th>Image Previews</th><th>Playlists</th><th>Plugins</th><th>Recipes</th><th>Docker</th><th>Test Suite</th><th>Maintained</th><th>Semantic Versioning</th></tr></thead><tbody><tr><td><a href="https://github.com/usetrmnl/byos_hanami"><strong>TRMNL Terminus</strong></a> (Ruby + Hanami)</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟡</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_phoenix"><strong>TRMNL</strong></a> (Elixir + Phoenix)</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>⚪️</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_sinatra"><strong>TRMNL</strong></a> (Ruby + Sinatra)</td><td>🟡</td><td>🔴</td><td>🟡</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🟢</td><td>⚫️</td><td>🟢</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_django"><strong>Community</strong></a> (Python + Django)</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🔴</td><td>🟢</td><td>⚪️</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_laravel"><strong>Community</strong></a> (PHP + Laravel)</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_next"><strong>Community</strong></a> (Next.js)</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🟢</td><td>⚪️</td></tr></tbody></table>

The following provides a detailed breakdown of each of the above features:

* **Dashboard**: Provides a high level overview of information mostly in terms of quick links, statistics, charts, graphs, system health, etc.
* **Auto-Provisioning**: Devices can be automatically provisioned once added to your network. This includes the automatic provisioning of new and existing devices.
* **Devices**: Provides device management in terms of updating each device, viewing current image, viewing logs, and more.
* **JSON Data API**: Provides full API support using a JSON Data API for device management, image generation, logging, and more.
* **Image Previews**: Provides a UI for quickly, and dynamically, generating new device screens.
* **Playlists**: Supports playlist configuration and management in terms of timing, order, and display of screens on devices. This can also include proxying to our Core server.
* **Plugins**: Supports installation and hosting of custom plugins. This can also include proxying to our Core server.
* **Recipes**: Supports installation and hosting of custom plugins. This can also include proxying to our Core server.
* **Docker**: Supports Docker for both local development and production deployment.
* **Test Suite**: Has a test suite with near 100% test coverage, is fully runnable locally, and is wired up with automatic Continuous Integration (CI) builds.
* **Maintained**: Project is maintained and kept up-to-date on a weekly (or monthly) basis in terms of dependencies, firmware updates, and keeping up-to-date with any/all Core changes.
* **Semantic Versioning**: Supports [strict semantic versioning](https://alchemists.io/articles/strict_semantic_versioning).

### API

At a minimum, the following API endpoints should be supported for all BYOS implementations:

#### Display

```bash
curl "http://byos.local/api/display" \
     -H 'Access-Token: <api_key>' \
     -H 'Accept: application/json' \
     -H 'Content-Type: application/json'
```

#### Images

```bash
curl -X "POST" "http://byos.local/api/images" \
    -H 'Access-Token: <api_key>' \
    -H 'Accept: application/json' \
    -H 'Content-Type: application/json' \
    -d $'{
 "image": {
   "content": "<p>Demo</p>"
   "file_name": "demo"
 }
}'
```

#### Logs

```bash
curl "http://byos.local/api/log" \
     -H 'Access-Token: <api_key>' \
     -H 'Accept: application/json' \
     -H 'Content-Type: application/json'
```

#### Setup

```
curl "https://byos.local/api/setup/" \
    -H 'ID: <mac:address:of:the:device>' \
    -H 'Accept: application/json' \
    -H 'Content-Type: application/json'

```

💡 For a detailed breakdown of all API endpoints and what they can do, please refer to the [Terminus API Documentation](https://github.com/usetrmnl/byos_hanami?tab=readme-ov-file#apis) or the [TRMNL API](https://github.com/usetrmnl/trmnl-api) gem which provides a Ruby API client for talking to our servers.

