## editSubscription - Call of a Subscription

```http
GET /api/v1/customer/customer_number/subscriptions/subscription_id/edit HTTP/1.1
```

```javascript
isaac10.editSubscription(subscription_id);
```

> Response

```json
{
  "plan": {
  },
  "billing_data": {
    "gender": "female",
    "title": "Dr.",
    "first_name": "Maxi",
    "last_name": "Mustermann",
    "company": "",
    "street": "Musterstraße 1",
    "zip": "12345",
    "city": "Musterstadt",
    "country": "DE",
    "ustid": "DE1234567890"
  },
  "payment_data": {
    "payment_method": "invoice"
  },
  "subscription": {
    "id": "2",
    "begins_at": "2015-09-24",
    "term_ends_at": "2015-10-23",
    "billing_interval": "yearly",
    "next_billing_interval": "yearly",
    "status": "ongoing",
    "additions": [
      {
        "nid": "NID addition 1",
        "name": "Name addition 1",
        "price": [
          { "interval": "monthly", "cents": "100" },
          { "interval": "quarterly", "cents": "400" },
          { "interval": "yearly", "cents": "1200" }
        ],
        "quantifiable": "false",
        "quantity": "0",
        "next_quantity": "0"
      },
      {
        "nid": "NID addition 2",
        "name": "Name addition 2",
        "price": [
          { "interval": "monthly", "cents": "100" },
          { "interval": "quarterly", "cents": "400" },
          { "interval": "yearly", "cents": "1200" }
        ],
        "quantifiable": true,
        "quantity": "0",
        "next_quantity": "0"
      }
    ]
  },
  "allowed_transitions": [
    {
      "nid": "NID of the current plan",
      "name": "Name of the current plan",
      "transition_type": "self"
    }
  ]
}
```


<aside class="success">
Before the function request, the <a href= "#customer-authentication"> customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.  
**subscription_id** | The ID of the subscription.

### Response

Parameter | Description
----------|-------------
**plan** | This data is the same as provided when calling `.getPlan()`.
**billing_data** | Data of the customer's billing address.
**payment_data** | Data of the given payment method.
**subscription** | Data of the created subscription.
**allowed_transitions** | Additional information for Upgrading/Downgrading.
