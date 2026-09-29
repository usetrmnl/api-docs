---
description: Stub a device + discount code with the Partners API.
---

# Provisioning Devices

To preload a custom plugin on a device for your customer, you can generate a coupon code and share the customer's relevant credentials in a single API request.

**Step 1 - Partner requests a coupon**

```
POST https://trmnl.com/api/partners

Headers:
Client-Id, Access-Token # provided by TRMNL team
Content-Type: application/json

Body:
{
  "partner": {
    "action": "provision_discount",
    "data": { "user-data": "goes here", "more-data": "also ok" },
    "meta": { "expires_at": "2025-03-20" } # optional, see below
  }
}
```

TRMNL generates a single-use coupon with your Partner name + a timestamp suffix.

```
# response example
{ "status": 200, "data": { "code": "acme-1733187331" } }
```

* `expires_at` -- the code stops working at 23:59 US Eastern time on this date. Leave it out and the code expires 90 days from today.
* `action` -- `provision_discount` is the only action today. Any other value returns `{ "status": 200, "data": null }`.
* Each code works once, for one customer.

{% hint style="warning" %}
**Check the body, not the HTTP status.** Every response comes back as HTTP `200`. If your `Client-Id` + `Access-Token` pair is wrong, the body is `{ "status": 403 }` and no code is created.
{% endhint %}

**Step 2 - Customer redeems the coupon**

Provide the `code` from Step 1 to your customer with instructions to purchase a device from trmnl.com. They can provide this code at checkout.

The discount itself follows your program terms (see [Getting Started](getting-started.md)). You will be billed via invoice later for claimed discount codes during the agreed period. Additional terms are possible, for example requiring customers to pay for shipping, or only subsidizing a device with our regular (vs large size) battery, etc.

**Step 3 - TRMNL pre-loads the Partner's plugin**

Prior to this workflow being implemented, TRMNL should have already tested your custom plugin. Assuming it requires some kind of API credential to be accessed by a TRMNL user's device, the Step 1 payload should include these details inside the `data` node.

Here's what happens next:

1. We assemble the customer's device + link it to the order that used your code.
2. The customer pairs the device to WiFi. When it finishes setup with our server, we copy your plugin setting into their account and add it to the device's playlist, refreshing every 15 minutes.
3. The key/values from your `data` node are saved as that copy's (encrypted) settings.

We store `data` exactly as sent, replacing any encrypted settings your own plugin setting carries. Thus these key/values should match exactly what your plugin reads -- we'll agree the key layout with you while testing your plugin.

Contact [partners@trmnl.com](mailto:partners@trmnl.com) with questions or requests.
