---
description: Open endpoints that don't require authentication.
---

# Introduction

{% hint style="info" %}
Every endpoint, parameter + response shape lives in our [API reference](https://trmnl.com/api-docs), generated from our code + always current.
{% endhint %}

Whether you have a native TRMNL with Developer Edition, a BYOD license, or no device at all, you may benefit from publicly available data in JSON format.

No API key, no account. Just `GET` (or `POST` where noted) the URL. Full request + response schemas live in our [API docs](https://trmnl.com/api-docs).

| Endpoint | What you get |
| -------- | ------------ |
| `GET` [/recipes.json](https://trmnl.com/recipes.json) | Search + sort community plugins ([guide](recipes-api.md)) |
| `GET` `/recipes/{id}.json` | One community plugin ([guide](recipes-api.md#get-a-single-recipe)) |
| `GET` [/api/categories](https://trmnl.com/api/categories) | Valid plugin categories ([guide](categories-api.md)) |
| `GET` [/api/models](https://trmnl.com/api/models) | Supported [device models](https://trmnl.com/api-docs) -- dimensions, colors, bit depth, palettes + Framework CSS classes |
| `GET` [/api/palettes](https://trmnl.com/api/palettes) | Color palettes referenced by each model's `palette_ids` |
| `POST` `/api/markup` | Render a [Liquid](https://help.trmnl.com/en/articles/10671186-liquid-101) template with TRMNL's filters. Send `markup` (a string or an array of strings) + optional `variables` |
| `GET` [/api/ips](https://trmnl.com/api/ips) | IPv4 + IPv6 addresses of our servers. Plugin poll requests only come from these, so allowlist them behind a firewall |
| `GET` [/api/firmware/latest](https://trmnl.com/api/firmware/latest) | Latest production firmware for TRMNL OG -- `model`, `version` + `url` to the binary |
| `GET` [/api/firmware/flash](https://trmnl.com/api/firmware/flash) | Every published firmware version per model, as used by our [web flasher](https://trmnl.com/flash) |
| `GET` [/api/bounties](https://trmnl.com/api/bounties) | Open community bounties. Add `?completed=true` for finished ones |
| `/api/book/{token}/...` | Walk-up room booking. The `token` comes from a room's public booking link, so no account is needed |

{% hint style="info" %}
`/api/models`, `/api/palettes` and `/api/firmware/latest` are cached for 5 minutes. Everything else is served fresh.
{% endhint %}
