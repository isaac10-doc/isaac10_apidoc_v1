## List Customer Subscriptions

```http
GET /api/v1/customer/customer_number/subscriptions HTTP/1.1
```

```javascript
isaac10.getSubscriptions();
```

> Response

```json
{
  "subscriptions": [
    {
      "id":                     42,
      "product_name":          "name of the product",
      "plan_name":             "name of the plan",
      "plan_nid":              "abc123",
      "begins_at":             "2014-09-25",
      "term_ends_at":          "2014-10-24",
      "billing_interval":      "monthly",
      "next_billing_interval": "monthly",
      "status":                "ongoing",
      "currency":              "EUR",
      "pricing":               "brutto",
      "price":                  3000,
      "next_price":             3000,

      "additions": [
        {
          "nid":               "NID of the addition",
          "name":              "name of the addition",
          "begins_at":         "2014-09-25",
          "price":              200,
          "next_price":         200,
          "quantifiable":       true,
          "quantity":           2,
          "next_quantity":      1
        }, {
          ...
        }
      ],

      "total_price":            3400,
      "next_total_price":       3200
    }, {
      ...
    }
  ]
}
```

<aside class="success">
Before making the function call, the <a href="#customer-authentication">customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The ID of the customer.

### Response

An array of all subscriptions of the customer.

Parameter | Description
----------|------------
**begins_at** | The date when the subscription started.
**term_ends_at** | The date when the current term of the subscription ends.
**billing_interval** | The billing interval the customer has choosen for the current term: `monthly`, `quarterly` or `yearly`.
**next_billing_interval** | The billing interval that gets valid when the next term starts: `monthly`, `quarterly` or `yearly`.
**status** | _see table below_
**pricing** | Are prices gross or net? `brutto` for gross, `netto` for net (yes, these are the german terms).
**price** | Indication in cents for the current term of the subscription _without additions_.
**next_price** | Indication in cents for the next term of the subscription _without additions_.
**additions[]** | An array of all subscribed additions.
**additions[].begins_at** | The date when the addition was booked.
**additions[].price** | Indication in cents of the addition for the current term.
**additions[].next_price** | Indication in cents of the addition for the next term.
**additions[].quantifiable** | Is the addition quantifiable? `true` or `false`.
**additions[].quantity** | The subscribed quantity of the addition for the current term. Always `1` when the addition is not quantifiable.
**additions[].next_quantity** | The quantity of the addition for the next term. When `0` the addition will be canceled when the end of the term is reached.
**total_price** | Indication in cents for the current term of the subscription _including additions_.
**next_total_price** | Indication if cents for the next term of the subscription _including additions_.

### _status_

Value | Description
------|------------
`ongoing` | Subscription is active and not in cancellation
`canceled` | Subscription is canceled, end of contract not reached yet
`expired` | Subscription is canceled, end of the contract is reached
`future` | Subscription contract starts in the future
