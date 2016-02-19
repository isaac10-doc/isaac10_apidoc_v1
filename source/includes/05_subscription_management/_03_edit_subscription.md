## Edit a Subscription

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
    ...
  },
  "billing_data": {
    ...
  },
  "payment_data": {
    ...
  },
  "subscription": {
    ...
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
Before the function request, the <a href= "#customer-authentication"> customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|------------
**customer_number** (in URL) | The number identifying the customer.
**subscription_id** | The ID of the subscription.

### Response

Parameter | Description
----------|------------
**plan** | Data of the plan. Same as [Get Plan Data](#get-plan-data)
**billing_data** | Data of the customer's billing address. Same as [Get Account Data](#get-account-data)
**payment_data** | Data of the given payment method. Same as [Get Account Data](#get-account-data)
**subscription** | Data of the subscription to edit. Same as [List Customer Subscriptions](#list-customer-subscriptions)
**allowed_transitions[]** | Additional information for Upgrading/Downgrading.
**allowed_transitions[].nid** | The NID of the plan to which can be up- or downgraded.
**allowed_transitions[].name** | The name of the plan to which can be up- or downgraded.
**allowed_transitions[].transition_type** | _See table below_

### _transition_type_

Value | Description
------|------------
`upgrade` | Changing the subscription to this plan will be considered an _upgrade_ and therefor will be valid immediately.
`downgrade` | Changing the subscriptio to this plan will be considered a _downgrade_ and therefor will be valid when the end of the current term is reached.
`self` | The current plan. It is listed in the array for convenience reasons.
