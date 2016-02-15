## Register

```http
POST /api/v1/register HTTP/1.1
```

```javascript
isaac10.register(params);
```

> Request Body / Params

```json
{
  "register": {
    "plan_nid": "NID of the plan",
    "billing_interval": "yearly",

    "gender": "female",
    "title": "Dr.",
    "first_name": "Firstname",
    "last_name": "Lastname",
    "company": "Company",
    "street": "Street 42",
    "zip": "12345",
    "city": "City",
    "country": "DE",
    "ustid": "",

    "payment_method": "invoice",

    "additions": [
      { "nid": "NID addition 1", "quantity": 1 },
      { "nid": "NID addition 2", "quantity": 4 }
    ],

    "coupon_code": "",

    "email": "email@example.com",
    "password": "password",
    "double_opt_in": false
  }
}
```

### Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><strong>plan_nid</strong></td>
    <td>
      The NID of the plan.
      <ul>
        <li>required</li>
        <li>plan must exist for this this merchant</li>
        <li>plan must be enabled</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>billing_interval</strong></td>
    <td>
      The billing interval for the subscription.
      <ul>
        <li>required if plan is with costs</li>
        <li>allowed values: <em>monthly, quarterly, yearly</em></li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>payment_method</strong></td>
    <td>
      The payment method to use. The example shows <code>invoice</code>. For all
      payment methods and the instructions to integrate them, see
      <a href="#payment_methods">Payment Methods</a>.
      <ul>
        <li>required if plan is with costs</li>
        <li>
          for allowed values see <a href="#payment_methods">Payment Methods</a>
        </li>
      </ul>
    </td>
  </tr>
</table>

### Response

```json
{
  "customer_number": "000001",
  "customer_token": "abc123",
  "plan_nid": "abc123",
  "subscription_id": 42
}
```

Parameter | Description
----------|------------
**customer_number, customer_token** | The customer number and customer token of the newly created account. Unless you want to [use the login function of _isaac10_ for authenticating your users](#customer-login), you need to save these in your database for [authenticating your customers](#customer-authentication).
**plan_nid** | The NID of the subscribed plan.
**subscription_id** | The ID of the newly created subscription. You need it as a parameter for [confirming the subscription](#confirming-the-subscription-after-register).
