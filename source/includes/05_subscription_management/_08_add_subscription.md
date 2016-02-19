## Adding a new Subscription

```http
POST /api/v1/customer/customer_number/subscriptions HTTP/1.1
```

```javascript
isaac10.addSubscription(params);
```

> Request body / Params

> - without costs


```json
{
  "id": null,
  "subscription": {
    "plan_nid": "NID of the plan",
    "billing_interval": "monthly",
    "additions": [
      { "nid": "NID addition 1", "quantity": 1 },
      { "nid": "NID addition 2", "quantity": 4 },
    ]
  }
}
```

> - with costs (requires billing address/payment method)

```json
{
  "id": null,
  "subscription": {
    "plan_nid": "NID of the plan",
    "billing_interval": "monthly",
    "additions": [
      { "nid": "NID addition 1", "quantity": 1 },
      { "nid": "NID addition 2", "quantity": 4 },
    ],

    "gender":           "female",
    "title":            "",
    "first_name":       "Maxi",
    "last_name":        "Mustermann",
    "company":          "",
    "street":           "Musterstraße 1",
    "zip":              "12345",
    "city":             "Musterstadt",
    "country":          "DE",
    "ustid":            "",

    "payment_method": "invoice"
  }
}
```

> Response

```json
{
  "plan": {
  },
  "subscription": {
}
}
```


<aside class="success">
Before making the function call, the <a href="#customer-authentication">customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.  

<br>
<br>

If the plan is with costs and neither billing address nor paymemt method have been given by the customer, the following data has to be transmitted for the subscription of the plan. (see right side)

<aside class="notice">
If billing address and payment method are already given by the customer, this information will be ignored.
<br>
<strong> Updating the billing address and payment method is not possible by this API call. </strong>
</aside>

### Validation

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
        <li>plan must exist for this merchant</li>
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
    <td><strong>additions</strong></td>
    <td>
      Additions for the plan.
      <ul>
        <li>all additions must be related to the booked plan itself</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>gender</strong></td>
    <td>
      Gender of the subscribing customer.
      <ul>
        <li>required, when plan is with costs</li>
        <li>allowed values: <em>male, female</em></li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>first_name</strong></td>
    <td>
      First name of the customer.
      <ul>
        <li>required, when plan is with costs</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>last_name</strong></td>
    <td>
      Last name of the customer.
      <ul>
        <li>required, when plan is with costs</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>street</strong></td>
    <td>
      Street name of the customer's address.
      <ul>
        <li>required, when plan is with costs</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>zip</strong></td>
    <td>
      Zip code of the customer's address.
      <ul>
        <li>required, when plan is with costs</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>city</strong></td>
    <td>
      City of the customer's address.
      <ul>
        <li>required, when plan is with costs</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>country</strong></td>
    <td>
      Name of the country of the customer's address.
      <ul>
        <li>required, when plan is with costs</li>
        <li>must be a double-digit country code</li>
        <li>must be included in the tax list</li>
      </ul>
    </td>
  </tr>
  <tr>
   <td><strong>payment_method</strong></td>
    <td>
      The payment method to use. The example shows <code>invoice</code>. For all
      payment methods and the instructions to integrate them, see
      <a href="#payment-methods">Payment Methods</a>.
      <ul>
        <li>required if plan is with costs</li>
        <li>
          for allowed values see <a href="#payment-methods">Payment Methods</a>
        </li>
      </ul>
    </td>
  </tr>
</table>
