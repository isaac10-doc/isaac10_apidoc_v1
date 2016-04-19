## Updating a Subscription

```http
PATCH /api/v1/customer/customer_number/subscriptions/subscription_id HTTP/1.1
```

```javascript
isaac10.updateSubscription(subscription_id, params);
```

> Request body / Params

```json
{
  "subscription": {
    "billing_interval": "yearly",
    "additions": [
      { "nid": "NID Tarifergänzung 1", "quantity": "1" },
      { "nid": "NID Tarifergänzung 2", "quantity": "0" },
      { "nid": "NID Tarifergänzung 3", "quantity": "2" }
    ]
  }
}
```

> Response

```json
{
  "success": true
}
```

Change a subscription of a customer. All changes are saved (when valid), but not all take effect immediately.

### Changes that take effect immediately

-   Raising the quantity of an addition
-   Adding an addition (i.e. raising the quantity of a non-subscribed addition above 0)

### Changes that take effect when the next term starts

-   Changing the billing interval
-   Lowering the quantity of an addition
-   Cancelation of an addition (i.e. lowering the quantity of a subscribed addition to 0)

<aside class="success">
Before making the function call, the <a href="#customer-authentication">customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.
**subscription_id** (in URL) | The ID of the subscription.
**next_billing_interval** | The period of billing, offered by the merchant. <ul><li>required</li><li>possible values: `monthly`, `quarterly`, `yearly`</li><li>The billing interval must be enabled for the subscription (See also: [Enabled billing intervals](#enabled-billing-intervals))</li></ul>
**additions** | The addition for a plan. <ul> <div style="text-align: left;"> <li> an addition with the given **nid** must exist for the plan to be changed </li><li> **quantify** must be a natural number </li></ul>
