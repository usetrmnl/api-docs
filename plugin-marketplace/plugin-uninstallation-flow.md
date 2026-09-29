---
description: Handling user uninstallation requests on your web server.
---

# Plugin Uninstallation Flow

<figure><img src="../.gitbook/assets/Screenshot 2024-09-06 at 3.36.35 PM.png" alt=""><figcaption></figcaption></figure>

When a user uninstalls your plugin, as a best practice TRMNL will send a notification via webhook. The POST request is sent to the `uninstallation_webhook_url` in JSON format with the following details:

HTTP Headers:

```
Authorization: Bearer <access_token>
Content-Type: application/json
```

Body:

<pre class="language-json"><code class="lang-json"><strong>{"user_uuid": "uuid-of-the-user"}
</strong></code></pre>

Parse this webhook payload to perform a "teardown" or similar strategy on your web server.

The `user_uuid` matches the `uuid` from the [Installation Flow](plugin-installation-flow.md) success webhook, and the Bearer token is the same `access_token` from the token exchange.

We send this webhook from a background job after the user deletes the instance. We wait up to 10 seconds for a response and don't retry: if your server is down, the event is gone, so don't rely on it as your only cleanup path. Uninstallation webhook URLs containing `http://localhost` are skipped entirely.
