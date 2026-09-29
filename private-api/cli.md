---
description: Every Account API endpoint as a command, from your terminal.
---

# CLI

The [TRMNL CLI](https://github.com/usetrmnl/cli) turns our [Account API](account.md) into commands -- list devices, rename them, manage playlists + plugin settings, install recipes, and more. 140 commands today.

**We don't ship a new CLI version when we add an endpoint.** The CLI reads our [OpenAPI document](https://trmnl.com/api-docs/openapi.json) and builds its commands from it, so new endpoints show up on their own. It's powered by [Restish](https://rest.sh), an open source HTTP client for OpenAPI services.

## Install

```sh
brew install usetrmnl/tap/trmnl
```

No Homebrew? Download a binary for macOS, Linux or Windows from [Releases](https://github.com/usetrmnl/cli/releases), or build it with Go:

```sh
go install github.com/usetrmnl/cli/cmd/trmnl@latest
```

## Sign in

The first command that touches your account opens trmnl.com in your browser. You'll see the same consent screen as any [connected app](https://trmnl.com/auth.md) -- pick what the CLI may do, click Allow, done.

| Capability | Lets the CLI | Ticked by default |
| --- | --- | --- |
| `read` | Read your devices + their logs, playlists, plugin settings + private plugin files | Yes |
| `content` | Change your markup, plugin settings, playlists + mashups, install recipes + push images | Yes |
| `devices` | Change your device settings + identify a device | Yes |
| `delete` | Delete plugin settings + playlist items, clear a device playlist | No |
| `profile` | See + change your name, time zone + display settings | No |
| `apps` | Install + manage apps, including fleet pushes + room bookings | No |

You can also limit the CLI to specific devices + plugin settings on that screen. Tokens refresh on their own -- use the CLI at least once every 30 days + you stay signed in. After a longer break it asks again.

**Changed your mind?** Remove "TRMNL CLI" under [Account > Connected agents](https://trmnl.com/account) and it loses access immediately. To sign out locally, run `trmnl auth logout`.

### API keys (scripts + CI)

No browser? Create an API key under [Account API keys](https://trmnl.com/account), give it only the capabilities it needs, then:

```sh
export TRMNL_API_KEY=trmnl_xxxxx
trmnl list-devices
```

When `TRMNL_API_KEY` is set, the CLI uses it and never opens a browser.

{% hint style="info" %}
The API keys section appears once your account has a device with the [Developer edition](https://shop.trmnl.com/products/developer-edition) upgrade (every [BYOD license](https://shop.trmnl.com/products/byod) includes it). Browser sign in works for every account.
{% endhint %}

## Usage

```sh
trmnl --help                        # every command, grouped like our API docs
trmnl list-devices --help           # parameters + body fields for one command
trmnl list-devices
trmnl update-device 123 'name: Kitchen'
```

Request bodies use Restish's [shorthand](https://rest.sh/#/shorthand) (`'name: Kitchen, sleep_mode_enabled: true'`), or pipe JSON in over stdin.

Output is JSON by default. Filter it + turn it into a table:

```sh
trmnl list-devices -f 'body.data' -o table --rsh-columns id,name,friendly_id
```

{% hint style="info" %}
The device API (`/api/display`, `/api/setup`, `/api/log`) is not part of the CLI. Those endpoints are for devices, authenticated with a device's own `Access-Token` -- see [Display API](screens.md).
{% endhint %}

## Errors

The CLI shows our API's answer as-is. The common ones:

* `403` naming a capability, e.g. "This API key lacks the devices capability" -- create a key with it, or remove "TRMNL CLI" from Connected agents + sign in again with that box ticked.
* `401 Invalid API key` -- `TRMNL_API_KEY` is wrong or revoked.
* `429` -- you hit the [rate limit](account.md). Wait a minute.

The CLI exits with a non-zero status on any error, so scripts can check `$?`.

## Good to know

* Config + tokens live in `~/.config/trmnl`, the command cache in `~/.cache/trmnl`
* New endpoint not showing up yet? `trmnl cache clear`
* Building a plugin? Use [trmnlp](https://github.com/usetrmnl/trmnlp) to preview your markup locally
* Want an AI agent to drive instead? Connect it to our [MCP server](https://help.trmnl.com/en/articles/14130438-ai-agent)

Most CLI "feature requests" are really API requests. If a command is missing or clunky, [let us know](https://github.com/usetrmnl/cli/issues) what you're trying to do + we'll improve the endpoint.
