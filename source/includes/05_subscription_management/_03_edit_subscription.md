## Edit a Subscription

Retrieve all necessary data to display an edit form for the subscription with the given `subscription_id` and a table with all possible up- and downgrade options.

```http
GET /api/v1/customer/<customer_number>/subscriptions/<subscription_id>/edit HTTP/1.1
```

```javascript
isaac10.editSubscription(subscription_id);
```

> Response

```json
{
  "plan": {
    ...
  },
  "billing_data": {
    ...
  },
  "payment_data": {
    ...
  },
  "subscription": {
    "id":                     42,
    "product_name":          "name of the product",
    "plan_name":             "name of the plan",
    "begins_at":             "2014-09-25",
    "term_ends_at":          "2014-10-24",
    "billing_interval":      "monthly",
    "next_billing_interval": "monthly",
    "status":                "ongoing",
    "currency":              "EUR",
    "pricing":               "brutto",

    "monthly_price":           3000,
    "quarterly_price":         null,
    "yearly_price":           48000,

    "additions": [
      {
        "nid":               "NID of the addition",
        "name":              "name of the addition",
        "begins_at":         "2014-09-25",
        "quantifiable":       true,
        "quantity":           2,
        "next_quantity":      1,

        "monthly_price":       100,
        "quarterly_price":    null,
        "yearly_price":       1200
      }, {
        ...
      }
    ]
  },
  "allowed_transitions": [
    {
      "nid": "NID of the current plan",
      "name": "Name of the current plan",
      "transition_type": "self"
    }, {
      "nid": "NID of another plan",
      "name": "Name of another plan",
      "transition_type": "upgrade"
    }, {
      "nid": "NID of another plan",
      "name": "Name of another plan",
      "transition_type": "downgrade"
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
----------|------------
**customer_number** (in URL) | The number identifying the customer.
**subscription_id** (in URL) | The ID of the subscription.

### Response

Parameter | Description
----------|------------
**plan** | Data of the plan. Same as [Request Plan Data](#request-plan-data)
**billing_data** | Data of the customer's billing address. Same as [Get Account Data](#get-customer-account-data)
**payment_data** | Data of the given payment method. Same as [Get Account Data](#get-customer-account-data)
**subscription** | Data of the subscription to edit.
**subscription.begins_at**<br>**subscription.term_ends_at**<br>**subscription.billing_interval**<br>**subscription.next_billing_interval**<br>**subscription.status**<br>**subscription.pricing** | Same as [Get Subscriptions](#get-subscriptions)
**subscription.price** | The prices for the possible billing intervals.
**subscription.additions[]** | An array of _all_ additions, both subscribed and unsubscribed.
**subscription.additions[].begins_at** | The date when the addition was booked. Is `null` when the addition is not booked.
**subscription.additions[].quantifiable** | Is the addition quantifiable? `true` or `false`.
**subscription.additions[].quantity** | The subscribed quantity of the addition for the current term. Is `0` when the addition is not subscribed. Is `1` when the addition is subscribed and not quantifiable.
**subscription.additions[].next_quantity** | The quantity of the addition for the next term. When `0` the addition is either unsubscribed or will be canceled when the end of the term is reached.
**subscription.additions[].price** | The prices for the possible billing intervals of the addition. The allowed billing intervals will match those of the subscription itself (see above).
**allowed_transitions[]** | Additional information for Upgrading/Downgrading. The table includes _all_ possible plans for up- and downgrading the subscription.
**allowed_transitions[].nid** | The NID of the plan to which can be up- or downgraded.
**allowed_transitions[].name** | The name of the plan to which can be up- or downgraded.
**allowed_transitions[].transition_type** | _See table below_

### _transition\_type_

Value | Description
------|------------
`upgrade` | Changing the subscription to this plan will be considered an _upgrade_ and therefore will be valid immediately.
`downgrade` | Changing the subscriptio to this plan will be considered a _downgrade_ and therefore will be valid when the end of the current term is reached.
`self` | The current plan. Listed in the array for convenience reasons.

<aside class="notice">
The response contains prices from the plan (in the <code>plan</code> hash) and the subscription (in the <code>subscription</code> and <code>subscription.additions[]</code> hashes). These prices may differ since you can override the prices set in the plan for any specific subscription and addition of a customer.
</aside>
