---
description: Handling user uninstallation requests on your web server.
---

# Plugin Uninstallation Flow

<figure><img src="../.gitbook/assets/Screenshot 2024-09-06 at 3.36.35 PM.png" alt=""><figcaption></figcaption></figure>

When a user uninstalls your plugin, as a best practice TRMNL will send a notification via webhook. The request is sent to the `uninstallation_webhook_url` in JSON format with the following details:

HTTP Headers:

```
{ 'Authorization': 'Bearer <access_token>', 'Content-Type': 'application/json'
```

Body:

```
{ 
  "user_uuid": "uuid-of-the-user"
}
```

Parse this webhook payload to perform a "teardown" or similar strategy on your web server.
