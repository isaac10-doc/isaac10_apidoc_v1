## updatePaymentData - Updating the Customer's Payment Method

```http
PATCH /api/v1/cstomer/customer_number/account/billing_data HTTP/1.1
```

```javascript
isaac10.updatePaymentData(params);
```

> Request body/ params

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
Before the function request, the customer must be authenticated.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.

### Validation
Parameter | Description
----------|-------------
**payment_method** | The payment method chosen by the customer. <ul> <div style="text-align: left;"> <li>required</li> <li>allowed values: see [Payment Methods](#payment_methods)</li> </ul>
