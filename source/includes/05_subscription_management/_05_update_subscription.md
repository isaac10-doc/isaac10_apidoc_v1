## updateSubscription - Updating a Subscription


```http
PATCH /api/v1/customer/customer_number/subscriptions/subscription_id HTTP/1.1
```

```javascript
isaac10.updateSubscription(subscription_id, params);
```

> Request body/params

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

<aside class="success">
Before the function request, the customer must be authenticated.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.  
**subscription_id** | The ID of the subscription.

### Validation
Parameter | Description
----------|-------------
**next_billing_interval** | The period of billing, offered by the merchant. <ul> <div style="text-align: left;"> <li>  required </li><li>  possible values: `monthly`, `quarterly`, `yearly` </li>  <li> The billing interval must be enabled for the plan </li></ul>
**additions** | The addition for a plan. <ul> <div style="text-align: left;"> <li> an addition with the given **nid** must exist for the plan to be changed </li><li>  **quantify** must be a natural number </li></ul>
