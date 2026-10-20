---
description: Let your server take its time. TRMNL asks for data, your server answers 202, then sends the data back when it is ready.
---

# Async Polling

{% hint style="info" %}
#### Before you begin

Learn how to build Private Plugins [here](https://help.trmnl.com/en/articles/9510536-custom-plugins). The guide below only explains how to use the "Async Polling" data retrieval strategy.
{% endhint %}

Use Async Polling when your data takes a while to produce: a report that runs for a few minutes, a slow scrape, a job on a queue. With Polling, TRMNL waits on the request until your server answers with the data. With Async Polling, your server answers at once, does the work, and sends the data back when it has it.

### How it works

1. On each refresh, TRMNL sends a request to your Polling URL. The request carries a one-time callback URL.
2. Your server answers `202 Accepted` at once, then starts the work.
3. When the data is ready, your server POSTs it to the callback URL. It has 15 minutes.
4. TRMNL renders a new screen from the data. The next refresh starts the cycle again.

Until a callback arrives, your plugin keeps showing the last data it received.

### Requirements

The device that owns the plugin must have Developer edition enabled. Without it, callbacks receive a `403`.

### Set up the plugin

Create a Private Plugin, set **Strategy** to **Async Polling**, and put `{{ callback_url }}` in your **Polling URL**, where your server expects to read it. TRMNL refuses to save an Async Polling plugin without it. A query parameter is easiest:

```
https://example.com/reports/start?callback={{ callback_url | url_encode }}
```

Your server receives something like this:

```
GET https://example.com/reports/start?callback=https%3A%2F%2Ftrmnl.com%2Fapi%2Fasync_callbacks%2Fasdfqwerty1234%3Fv%3D7
```

A few things to know:

* `{{ callback_url }}` also works in Polling Headers and Polling Body, if your server prefers to read it there.
* Polling Verb, Polling Headers and Polling Body work as they do for Polling. With `GET`, the body is sent as query parameters.
* Only the first line of the Polling URL is used. Async Polling makes one request per refresh.
* The **Test request** button sends a callback URL without a version. A callback to it receives `410`, so a test never changes your screen. Test the full cycle with a real refresh.

{% hint style="warning" %}
**Do not save a callback URL in your server.** Each request carries its own version, and a callback to any other version receives `410 Version mismatch`. Use the `callback_url` that arrived with the request.
{% endhint %}

### Answer with 202

Your server must answer the polling request with HTTP `202`. Any other status ends the cycle, `200` included: TRMNL marks the plugin as erroring and keeps the last data. A timeout or a connection error does the same.

If your server can answer with the data in a normal request, use Polling instead. It is simpler.

### Send the data

POST to the callback URL, with the data inside a `merge_variables` node. This is the same shape as a [Webhook](webhooks.md):

```
curl "https://trmnl.com/api/async_callbacks/asdfqwerty1234?v=7" \
  -H "Content-Type: application/json" \
  -d '{"merge_variables": {"revenue": "$12,400", "orders": 87}}' \
  -X POST
```

A successful callback receives `200` with `{"status": "ok"}`, and TRMNL starts to render the new screen at once.

* Each callback URL works once. The `v` number changes on every refresh, so use the whole URL as you received it.
* A callback replaces all merge variables. The Webhook `deep_merge` and `stream` strategies do not apply.
* Transform scripts do not run for Async Polling. Shape the data on your server before you send it.

### Limits

_Request size_

You may send up to 5kb of merge variables. [TRMNL+](https://help.trmnl.com/en/articles/11861887-trmnl-faq) subscribers may send up to 10kb. Larger payloads receive a `422` response with the size we measured.

_Request volume_

You may send up to 12 callbacks per hour per plugin. TRMNL+ subscribers, and plugins with "Debug Logs" enabled, may send up to 30. Faster callbacks receive a `429` response.

_Time_

Your server has 15 minutes from the polling request to send the callback. After that, the callback receives `410` and the plugin log shows "Async callback not received within 15 minutes". TRMNL checks for expired requests every 5 minutes, so this entry can appear up to 5 minutes late.

### While a request is pending

While TRMNL waits for a callback, refreshes do not call your server again. This includes a manual refresh. A slow server is never asked twice at once, and a server that never answers holds the plugin for up to 20 minutes: the 15 minute window, plus up to 5 minutes until the next expiry check.

Changing the plugin's Strategy cancels a pending request. Other changes to the plugin settings leave it pending.

### Callback responses

| Status | Meaning |
| ------ | ------- |
| `200`  | Accepted. TRMNL renders a new screen. |
| `403`  | The device that owns the plugin does not have Developer edition enabled. |
| `404`  | No plugin has this UUID. |
| `410`  | The request is not pending anymore: expired, already answered, superseded by a newer request, or the Strategy is not Async Polling. The `message` field says which. Do not retry. Wait for the next polling request. |
| `422`  | The body has no `merge_variables` object, or the payload is too large. |
| `429`  | Too many callbacks this hour. |

## Troubleshooting

**Every callback receives `410 Version mismatch`.** Your server posts to a saved callback URL, or to one from an earlier request. Use the `callback_url` from the latest polling request.

**A callback receives `410 No pending async request`.** TRMNL already accepted a callback for this request, the request expired, or the Strategy changed. Each callback URL works once.

**The plugin shows "Async polling failed: HTTP 200".** Your server answered the polling request with the data. Answer `202` and send the data to the callback URL, or switch the plugin to Polling.

**The screen never changes, and there is no error on the plugin.** Check the plugin log for "Async callback not received within 15 minutes". Your server must POST within 15 minutes of the polling request.

For more help, see our [Private Plugin guide](https://help.trmnl.com/en/articles/9510536-custom-plugins) or join the developer Discord from your account tab.
