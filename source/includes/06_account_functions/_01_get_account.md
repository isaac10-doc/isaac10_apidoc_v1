## Get Customer Account Data

```http
GET /api/v1/customer/<customer_number>/account HTTP/1.1
```

```javascript
isaac10.getAccount();
```

> Response

```json
{
  "account": {
    "account_data": {
      "email":           "email@example.com"
    },

    "billing_data": {
      "gender":          "female",
      "title":           "",
      "first_name":      "Maxi",
      "last_name":       "Mustermann",
      "company":         "Company",
      "addition":        "Accounts Department",
      "street":          "Musterstraße 1",
      "zip":             "12345",
      "city":            "Musterstadt",
      "country":         "DE",
      "ustid":           "DE1234567890"
    },

    "payment_data": {
      "payment_method":  "invoice"
    },

    "payment_data_logos": ["visa", "mastercard"],
    "payment_data_types": ["invoice", "cc_paymill", "elv_paymill"]
  }
}
```

<aside class="success">
Before making the function call, the <a href="#customer-authentication">customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|------------
**customer_number** (in URL) | The number identifying the customer.

### Response

Parameter | Description
----------|------------
**billing_data** | The billing data of the customer. When no billing address present, the returned value is `"none"`.
**payment_data** | Specific data requested according to the method chosen. When returned it will _always_ contain a `payment_method` field. Further fields depend on the payment method used. See the [Payment Methods chapter](#payment-methods) for further information. When no payment data present, the returned value is `"none"`.
**payment_data_logos** | Logos of the different types of payment methods: <ul> <li>Visa</li> <li>Master Card</li> <li>American Express</li> <li>PayPal</li> </ul>
**payment_data_types** | All possible payment methods of the merchant. Included for convenience reasons.
