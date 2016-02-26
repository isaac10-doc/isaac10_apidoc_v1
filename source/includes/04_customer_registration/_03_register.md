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

    "locale": "de"
  }
}
```

### Parameters

Parameter | Description
----------|------------
**plan_nid** | The NID of the plan. <ul> <li>required</li> <li>plan must exist for this merchant</li> <li>plan must be enabled</li> </ul>
**billing_interval** | The billing interval for the subscription. <ul> <li>required if plan is with costs</li> <li>allowed values: <code>"monthly", "quarterly", "yearly"</code></li> </ul>
**additions** | Additions for the plan. <ul> <li>all additions must be related to the booked plan itself</li> </ul>
**gender** | Gender of the subscribing customer. <ul> <li>required, when plan is with costs</li> <li>allowed values: <em>male, female</em></li> </ul>
**first_name** | First name of the customer. <ul> <li>required, when plan is with costs</li> </ul>
**last_name** | Last name of the customer. <ul> <li>required, when plan is with costs</li> </ul>
**street** | Street name of the customer's address. <ul> <li>required, when plan is with costs</li> </ul>
**zip** | Zip code of the customer's address. <ul> <li>required, when plan is with costs</li> </ul>
**city** | City of the customer's address. <ul> <li>required, when plan is with costs</li> </ul>
**country** | Name of the country of the customer's address. <ul> <li>required, when plan is with costs</li> <li>must be a double-digit country code</li> <li>must be included in the tax list</li> </ul>
**payment_method** | The payment method to use. The example shows `invoice`. For all payment methods and the instructions to integrate them, see [Payment Methods](#payment-methods) <ul> <li>required if plan is with costs</li> <li>for allowed values see <a href="#payment-methods">Payment Methods</a> </li> </ul>
**coupon_code** | Code number of the coupon. <ul> <li>optional</li> <li>if coupon code is transferred, must be valuable and activated</li> </ul>
**email** | Mail adress of the customer. <ul> <li>required</li> <li>has to contain the `@` character</li> <li>must not have already been assigned to this subdomain or this merchant</li> </ul>
**password** | Customer's password for Login. <ul> <li>required</li> <li>must contain at least 6 characters</li> </ul>
**locale** | The language of the customer. <ul><li>optional (default: <code>"de"</code>)</li><li>allowed values: <code>"de", "en", "fr", "it", "es"</code></li></ul> When used in the JavaScript library and **locale** is not passed, the transmitted locale of the browser is used.

### Response

> Response

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
**customer_number, customer_token** | The customer number and customer token of the newly created account. Unless you want to [use the login function of _isaac10_ for authenticating your users](#customer-authentication), you need to save these in your database for [authenticating your customers](#customer-authentication).
**plan_nid** | The NID of the subscribed plan.
**subscription_id** | The ID of the newly created subscription. You need it as a parameter for [confirming the subscription](#confirmation-after-registration).
