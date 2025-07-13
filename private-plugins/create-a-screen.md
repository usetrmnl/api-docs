---
description: Leverage RESTful endpoints to generate custom screens on your TRMNL device.
---

# Create a screen

{% hint style="info" %}
### Before you begin

Creating screens requires a Private Plugin instance inside your TRMNL account. This is currently available via the web interface only. Simply navigate to [Plugins > Private Plugin > New](https://usetrmnl.com/plugin_settings/new?keyname=private_plugin).
{% endhint %}

If your private plugin's "Strategy" is set to Webhook, you can provide data to TRMNL's server up to 12x per hour. Requests sent at a faster pace will receive a `429` rate limit response.

### Authorization

TRMNL has Device API Keys, User API Keys, and Plugin Setting UUIDs. For private plugin screen generation, we'll use your Plugin Settings UUID.

This is accessible from your plugin instance's configuration form, in a field called Webhook URL.

<figure><img src="../.gitbook/assets/TRMNL Private Plugin Webhook URL w UUID.png" alt=""><figcaption><p>Private Plugin Webhook URL w/ UUID</p></figcaption></figure>

{% hint style="info" %}
**Note:**  you must "save" (create) a private plugin instance before a UUID and Webhook URL will be generated.
{% endhint %}

### Set new content

Send a `POST` request to your Webhook URL. Put data inside a `merge_variables` node like so:

```
curl "https://usetrmnl.com/api/custom_plugins/asdfqwerty1234" \
  -H "Content-Type: application/json" \
  -d '{"merge_variables": {"text":"You can do it!", "author": "Rob Schneider"}}' \
  -X POST
```

You will see this payload inside the Your Variables dropdown of the Markup Editor.

<figure><img src="../.gitbook/assets/TRMNL - Your Variables dropdown.png" alt=""><figcaption><p>Your variables - available inside the Markup Editor</p></figcaption></figure>

### Get merge variable content

To fetch existing `merge_variables` from a private plugin, `GET` from the same endpoint:

```
curl "https://usetrmnl.com/api/custom_plugins/asdfqwerty1234"
```

### Update existing content

If your private plugin needs to maintain state over time, for example an ever-growing todo list or a data visualization, you may prefer to send only "new" data points to your TRMNL plugin.

There are two strategies to accomplish this: `deep_merge`, and `stream`.

#### Deep merge strategy

The `deep_merge` strategy combines existing key/value pairs with the new values incoming on the webhook. It's a good way to update nested data with only a few values here and there.

```
curl "https://usetrmnl.com/api/custom_plugins/asdfqwerty1234" \
  -H "Content-Type: application/json" \
  -d '{"merge_variables": {"sensor": {"temperature": 42}}, "merge_strategy": "deep_merge"}' \
  -X POST
```

#### Stream strategy

The `stream` strategy is useful for accumulating values in arrays. Any top-level arrays are appended with the incoming values, and the `stream_limit` parameter ensures that old values drop off the arrays so they don't grow forever.

```
curl "https://usetrmnl.com/api/custom_plugins/asdfqwerty1234" \
  -H "Content-Type: application/json" \
  -d '{"merge_variables": {"temperatures": [40, 42]}, "merge_strategy": "stream", "stream_limit": 10}' \
  -X POST
```

Now you may iterate through the combined data inside your markup, for example:

<figure><img src="../.gitbook/assets/CleanShot 2025-05-28 at 14.33.07@2x.png" alt=""><figcaption></figcaption></figure>

## Create a screen (polling strategy)

If your private plugin's "Strategy" is set to Polling, the TRMNL server will periodically fetch for new data from an endpoint of your choice.

Simply provide 1 or more "Polling URL" inside your private plugin's configuration form, and TRMNL will make requests to those URLs. For quick testing, we've prepared an endpoint that responds with `text` and `author` key/value pairs, along with a `collection` array for quick demonstration:

[https://usetrmnl.com/custom\_plugin\_example\_data.json](https://usetrmnl.com/custom_plugin_example_data.json)

If your desired polling URL contains a collection/array in the root node, TRMNL will nest it inside a key named "data" for accessibility by the Liquid templating engine. Here is an example of that style payload:

[https://usetrmnl.com/custom\_plugin\_example\_data.json?collection\_only=true](https://usetrmnl.com/custom_plugin_example_data.json?collection_only=true)

{% hint style="info" %}
**Note**: With the Polling strategy, variables _do not_ need to be nested within a `merge_variables` node. That is only a requirement for the Webhook strategy.
{% endhint %}

## Troubleshooting

For more help, see our [Private Plugin guide](https://help.usetrmnl.com/en/articles/9510536-custom-plugins) or join the developer Discord from your account tab.
