---
description: Become a TRMNL Partner.
---

# Getting Started

The TRMNL team manually approves each Partner, which involves the following:

1. basic KYC to ensure our intentions align (_customer delight, not bulk discounts_)
2. program negotiation (net-30 vs on-demand payment terms, optional quotas, etc)
3. testing the Partner's custom plugin end-to-end

**KYC** includes determining a Partner point of contact, getting some sense of weekly / monthly device provision volume, and possibly a small deposit.

**Program negotiation** is simple and might look like this: "_Partner wants to award their customers a TRMNL device for 50% off. Partner can generate TRMNL discount codes for 50% off and will pay TRMNL monthly via invoice for the remaining 50%, less a 10% bulk discount._"

**Testing** entails the Partner providing TRMNL a demo user account on the Partner platform, with instructions to set up their custom plugin manually on an existing TRMNL account.

Once approved, we set you up on our side:

* your **Partner name** -- it becomes the prefix of every discount code you generate (`acme-1733187331`), so customers will see it
* a `Client-Id` + `Access-Token` pair for the [Partners API](provisioning-devices.md). Treat them like a password; anyone holding both can generate discount codes in your name
* your **plugin setting** -- the instance of your custom plugin, owned by your TRMNL account, that we copy onto each provisioned device

Next up: [Provisioning Devices](provisioning-devices.md).
