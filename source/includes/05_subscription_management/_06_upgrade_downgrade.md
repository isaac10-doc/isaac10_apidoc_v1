## upgradeDowngradeSubscription - Upgrading/Downgrading a Subscription


```http
POST /api/v1/customer/customer_number/subscriptions/subscription_id/upgrade_downgrade HTTP/1.1
```

```javascript
isaac10.upgradeDowngradeSubscription(subscription_id, params);
```



> Request body/params

```json
"subscription": {
  "plan_nid": "NID of the plan",
  "billing_interval": "monthly",
  "additions": [
    { "nid": "NID addition 1", "quantity": 1 },
    { "nid": "NID addition 2", "quantity": 4 },
  ]
}
```


```json
"subscription": {
  "plan_nid": "NID of the plan",
  "billing_interval": "monthly",
  "additions": [
    { "nid": "NID addition 1", "quantity": 1 },
    { "nid": "NID addition 2", "quantity": 4 },
  ],
  "gender":           "female",
  "title":            "",
  "first_name":       "Maxi",
  "last_name":        "Mustermann",
  "company":          "",
  "street":           "Musterstraße 1",
  "zip":              "12345",
  "city":             "Musterstadt",
  "country":          "DE",
  "ustid":            "",

  "payment_method": "invoice"
}
```




> Response

```json
{
  "success": {
    "subscription_id": 3793
  }
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


### Validations
The validations and conditions for an upgrade/downgrade are the same as mentioned in chapter [addSubscription() - Add a Subscription](#add_subscription).

The conditions for billing address and billing method as mentioned below are the same for this call and, if necessary, must be transferred.
