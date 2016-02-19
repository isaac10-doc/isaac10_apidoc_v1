## Call Customer and Plan data

```http
GET /api/v1/customer/customer_number/subscriptions/new?plan=plan_nid HTTP/1.1
```

```javascript
isaac10.getSubscribe(plan_nid);
```


> Response

```json
{
  "plan": {
  },
  "account": {
  }
}
```

<aside class="success">
Before the function request, the <a href= "#customer-authentication"> customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The ID of the customer.  
**plan_nid** | The NID of the plan.


Account data of the customer and plan data can be called up in the same request.


### Response

Parameter | Description
----------|-------------
**plan** | This data is the same as provided when calling `.getPlan()`.
**account** | This data is the same as provided when calling `.getAccount()`.
