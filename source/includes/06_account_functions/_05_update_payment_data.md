## updatePaymentData - Updating the Customer's Payment Method

```http
PATCH /api/v1/customer/customer_number/account/billing_data HTTP/1.1
```

```javascript
isaac10.updatePaymentData(params);
```

> Request body / Params

```json
{
  "payment_data": {
    "payment_method": "invoice"
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
Before the function request, the <a href= "#customer-authentication"> customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.

### Validation
Parameter | Description
----------|-------------
**payment_method** | The payment method chosen by the customer. <ul> <div style="text-align: left;"> <li>required</li> <li>allowed values: see [Payment Methods](#payment-methods)</li> </ul>
