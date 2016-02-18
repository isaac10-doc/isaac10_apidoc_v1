## updateAccountData - Updating the Customer's Account Data

```http
PATCH /api/v1/customer/customer_number/account/account_data HTTP/1.1
```

```javascript
isaac10.updateAccountData(params);
```

> Request body/ params

```json
{
  "account_data": {
    "email": "new_email@example.com"
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
**email** | The Email Address of the customer. <ul> <li>required</li> <li>has to contain the @ character</li> <li>must not have already been assigned to this subdomain or this merchant</li> </ul>
