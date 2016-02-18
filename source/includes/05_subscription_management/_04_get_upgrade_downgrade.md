## getUpgradeDowngradeSubscription - Call of Account, Subscription and Plan Data


```http
GET /api/v1/customer/customer_number/subscriptions/subscription_id/upgrade_downgrade/plan_nid HTTP/1.1
```

```javascript
isaac10.getUpgradeDowngradeSubscription(subscription_id, plan_nid);
```

> Response

```json
{
  "plan": {
  },
  "account": {
  },
  "subscription": {
    "id": "6",
    "begins_at": "2015-09-21",
    "term_ends_at": "2015-10-20",
    "billing_interval": "monthly",
    "next_billing_interval": "monthly",
    "status": "ongoing",
    "additions": []
  }
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
**plan_nid** | The NID of the plan.


### Response

Parameter | Description
----------|-------------
**plan** | This data is the same as provided when calling `.getPlan()`.
**account** | This data is the same as provided when calling `.getAccount()`.
**subscription** | Data of the created subscription.
