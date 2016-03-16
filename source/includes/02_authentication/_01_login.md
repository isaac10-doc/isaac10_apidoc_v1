## Login

```http
POST /api/v1/authenticate HTTP/1.1

{
  "email": "you@example.com",
  "password": "customer password"
}
```

```javascript
isaac10.login('email', 'password');
```

> Response

```json
{
  "success": {
    "customer_number": "100001",
    "customer_token":  "abc123",
    "confirmed":        true
  }
}

{
  "success": {
    ...
    "confirmed":                 false,
    "request_confirmation_url": "http://subdomain.isaac10.com/confirm/789"
  }
}
```

If you wish to outsource the customer authentication entirely to _isaac10_, you can request customer number and customer token, which are needed for the AUTHORIZE header or the JavaScript function `.authenticateCustomer()` (explained in [Customer Authentication](#customer-authentication)), with this API call.

If you are using the JavaScript library, `.authenticateCustomer()` will be called automatically with the returned customer number and customer token after the request returns successfully.

<aside class="notice">
There is no equivalent function for authenticating you as merchant.
</aside>

### Params

Parameter | Description
----------|------------
**email** | Email address of the customer. <ul><li>required</li></ul>
**password** | Password of the customer. <ul><li>required</li></ul>

If `email` and `password` are not matching, error 404 will be returned.

### Response

Parameter | Description
----------|------------
**customer_number**<br>**customer_token** | Customer number and customer token to be used for [Customer Authentication](#customer-authentication).
**confirmed** | Is the customer confirmed (i.e. clicked on the confirmation link send to her/him after the registration)? `true` or `false`.
**request_confirmation_url** | Only present when the customer is not confirmed. A GET request to this URL will trigger sending an email with the confirmation link to the customer.
