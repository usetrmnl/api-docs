---
description: Buy a TRMNL device, then point it at your own server.
---

# BYOS

First, purchase a TRMNL from our [store](https://trmnl.com). Then choose a BYOS implementation for your stack. Our flagship implementation is Terminus (Hanami), so we recommended you get started there. But you can also choose from other languages/frameworks.

**Why BYOS?**

TRMNL intends to ensure that **every device is un-brickable and can run with zero external dependencies**.

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

<table><thead><tr><th width="150.58984375">Implementation</th><th>Stack</th><th width="121.6953125">Dashboard</th><th width="172.37109375">Auto-Provisioning</th><th width="111.859375">Devices</th><th>JSON Data API</th><th>Image Previews</th><th>Playlists</th><th>Plugins</th><th>Recipes</th><th>Docker</th><th>Test Suite</th><th>Maintained</th><th>Semantic Versioning</th></tr></thead><tbody><tr><td><a href="https://github.com/usetrmnl/byos_hanami"><strong>Terminus</strong></a></td><td>Ruby/Hanami</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_laravel"><strong>BYOS Laravel</strong></a></td><td>PHP/Laravel</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td></tr><tr><td><a href="https://github.com/usetrmnl/inker"><strong>Inker</strong></a></td><td>JavaScript</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>⚪️</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_next"><strong>BYOS Next.js</strong></a></td><td>JavaScript/Next.js</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🟢</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_fastapi"><strong>BYOS Fast API</strong></a></td><td>Python/FastAPI</td><td>🟢</td><td>⚪️</td><td>🟢</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>⚪️</td><td>🔴</td><td>🔴</td><td>⚪️</td><td>⚪️</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_django"><strong>BYOS Django</strong></a></td><td>Python/Django</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🔴</td><td>🟢</td><td>⚪️</td></tr><tr><td><a href="https://github.com/usetrmnl/byos_phoenix"><strong>BYOS Phoenix</strong></a></td><td>Elixir/Phoenix</td><td>🔴</td><td>🔴</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🟢</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>🔴</td><td>⚪️</td></tr></tbody></table>

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

#### Setup

```shell
curl "https://byos.local/api/setup" \
    -H 'ID: <device_mac_address>' \
    -H 'Content-Type: application/json'
```

#### Display

```bash
curl "http://byos.local/api/display" \
     -H 'ID: <device_mac_address>' \
     -H 'Content-Type: application/json'
```

#### Logs

```bash
curl "http://byos.local/api/log" \
     -H 'ID: <device_mac_address>' \
     -H 'Content-Type: application/json'
```

💡 For a detailed breakdown of all API endpoints and what they can do, please refer to the [Terminus API Documentation](https://github.com/usetrmnl/byos_hanami?tab=readme-ov-file#apis) or the [TRMNL API](https://github.com/usetrmnl/trmnl-api) gem which provides a Ruby API client for talking to our servers.
