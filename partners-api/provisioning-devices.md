---
description: Stub a device + discount code with the Partners API.
---

# Provisioning Devices

To preload a custom plugin on a device for your customer, you can generate a coupon code and share the customer's relevant credentials in a single API request.

**Step 1 - Partner requests a coupon**

```
POST /api/partners

Headers: 
Client-ID, Access-Token # provided by TRMNL team

Body:
{ 
  partner: { 
    action: "provision_discount", 
    data: { "user-data": "goes here", "more-data": "also ok" },
    meta: { "expires_at": "2025-03-20" } # will expire at 23:59 EST on this date
  }
} 
```

Based on your program terms, TRMNL will generate a coupon with your Partner name + unique suffix.

```
# response example
{ status: 200, data: { code: "acme-123456789" } }
```

If a quota is preferred, for example 50x maximum provisions per month, this endpoint will return a `nil`code value when the quota is breached.

**Step 2 - TRMNL generates a coupon**

Provide the `code`from Step 1 to your customer with instructions to purchase a device from usetrmnl.com. They can provide this code at checkout.

If your discount is for 100% off, they will not be charged. If your code is for 50% off, they will pay 50% at checkout. You will be billed via invoice later for claimed discount codes during the agreed period. Additional terms are possible, for example requiring customers to pay for shipping, or only subsidizing a device with our regular (vs large size) battery, etc.

**Step 3 - TRMNL pre-loads the Partner's plugin**

Prior to this workflow being implemented, TRMNL should have already tested your custom plugin. Assuming it requires some kind of API credential to be accessed by a TRMNL user's device, the Step 1 payload should include these details inside the `data`node.&#x20;

Whatever key/values are provided in the `data`  node of Step 1 will be saved to the user's pre-loaded plugin when their device is unboxed and set up. Thus these key/values should match exactly the merge variables required by the plugin setting instance.

Contact [partners@usetrmnl.com](mailto:partners@usetrmnl.com) with questions or requests.
