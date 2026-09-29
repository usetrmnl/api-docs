---
description: Additional options to customize your setup.
---

# More Endpoints

Here's a map of what the [account API](account.md) covers, grouped the same way as our OpenAPI docs. Every request, parameter + response shape lives there:

[https://trmnl.com/api-docs](https://trmnl.com/api-docs) ([raw YAML](https://trmnl.com/api-docs/openapi.yaml))

Reading needs a key with the `read` capability; changes need `content`, `devices`, `delete`, `profile` or `apps` (see [capabilities](account.md#account-api-keys)). A `403` names whichever one is missing.

### Account

* **Users** -- read + update your name, locale, account name + notification preferences at `/api/me`
* **Devices** -- list, read + update devices, claim a new one, identify it, mirror another device, retry a firmware update, and read its logs, timeline, forecast + playlist coverage
* **Playlists** -- list, add, reorder, bulk update, duplicate + delete playlist items, copy a playlist to another device, and read or replace an item's schedule
* **Mashups** -- create a mashup on a device, change which plugins fill its sections, reset its health

### Plugins

* **Plugin Settings** -- list, create, update, copy + delete plugin instances, push webhook data, upload an image, set a featured image, clear state, reset credentials, and download or upload a plugin as a zip archive
* **Plugin Settings - Markup** -- read + write the Liquid markup for each layout size
* **Plugin Settings - Merge Variables** -- see what a plugin's markup can reference
* **Plugin Settings - Settings** -- change a plugin's form field values
* **Plugin Settings - Refresh** + **Preview** -- force a data refresh or render a screenshot, then poll for the result
* **Plugin Settings - Logs** -- read a plugin's logs, turn on debug logging
* **Plugins** -- the plugin catalog
* **Recipes** -- search [community recipes](https://trmnl.com/recipes), read their markup, install one
* **My Plugins** + **Analytics** -- for [plugin authors](../plugin-marketplace/introduction.md): the third-party plugins you're building, plus installs, forks, errors + uninstall feedback for everything you've published. Creating or updating a third-party plugin needs a Developer edition device
* **User Themes** -- create, import + edit your own themes

### Apps

* **Apps** -- list apps, install + uninstall them
* **Apps - Fleet** -- manage a device fleet: members, settings, alerts, a master device + pushes
* **Apps - Room Booking** -- calendars, collections, integrations, bookings, branding + billing for room displays

### No account key needed

* **Device API** -- `/api/display`, `/api/display/current` + `/api/log`, authenticated with a device's `Access-Token` (see [Display API](screens.md)). `/api/setup` is how a device trades its MAC address (`ID` header) for that token
* **Models**, **Palettes**, **Categories**, **Server IPs** + **Flash Firmwares** -- public reference data (see [Public API](../public-api/introduction.md))
* **Markup** -- render a Liquid template with your own variables
* **Public booking** -- list + make walk-up bookings for a room, authenticated by the token in its shared link
