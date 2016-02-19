## uncancelSubscription - Uncancel a Subscription


```http
DELETE /api/v1/customer/customer_number/subscriptions/subscription_id/revert HTTP/1.1
```

```javascript
isaac10.uncancelSubscription(subscription_id);
```

> Response

```json
{
  "success": true
}
```


<aside class="success">
Before making the function call, the <a href="#customer-authentication">customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.  
**subscription_id** | The ID of the subscription.
