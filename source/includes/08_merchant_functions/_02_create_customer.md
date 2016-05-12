## Create a new customer

```http
POST /api/v1/customers HTTP/1.1
```

```javascript
// not implemented, REST only
```

> Request body

```json
{
  "customer": {
    "email":    "customer@example.com",
    "password": "password",
    "locale":   "de"
  }
}
```

> Response

```json
{
  "success": {
    "customer_number": "100001",
    "customer_token":  "abc123"
  }
}
```

Create a new customer for the merchant. The created customer will not have a billing address, no payment information and no subscription. The customer is also created as _confirmed_ (i.e. no double-opt-in) and can therefore log in immediately after it's creation.

<aside class="warning">
Using this REST call will bypass the normal customer registration. <b>There will be no emails sent to the customer.</b>
</aside>

<aside class="success">
Before making the function call, you must <a href="#merchant-authentication">authenticate yourself</a>.
</aside>

### Params

Parameter | Description
----------|------------
**email,**<br>**password,**<br>**locale** | The email, password and locale for the new customer. See [Register](#register) for further details.

### Response

Parameter | Description
----------|------------
**customer_number,**<br>**customer_token** | The customer number und customer token of the created customer.
