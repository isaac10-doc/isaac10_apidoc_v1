## getSubscriptions - Call Customer's Subscriptions

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
      "id":               42,
      "product_name":     "Name of the products",
      "plan_name":        "Name of the plan",
      "begins_at":        "2014-09-25",
      "term_ends_at":     "2014-10-24",
      "billing_interval": "monthly",   
      "price":             3000,       
      "status":           "ongoing"    
    }
  ]
}
```

<aside class="success">
Before the function request, the customer must be authenticated.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The ID of the customer.  


### Response

Parameter | Description
----------|-------------
**billing_interval** | `monthly`, `quarterly` or `yearly`
**price** | Indication in cents
**status** | see table

### Status

Status | Description
----------|-------------
_ongoing_ | Subscription is active and not in cancellation
_canceled_ | Subscription is canceled, end of contract not reached yet
_expired_ | Subscription is canceled, end of the contract is reached
_future_ | Subscription contract starts in the future
