## updatePassword - Updating the Customer's Password

```http
PATCH /api/v1/customer/customer_number/account/password HTTP/1.1
```

```javascript
isaac10.updatePassword(params);
```

> Request body/ params

```json
{
  "password": {
    "password": "new_password"
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
**password** | The new password of the customer. <ul> <div style="text-align: left;"> <li>required</li> <li>must contain at least 6 characters</li> </ul>
