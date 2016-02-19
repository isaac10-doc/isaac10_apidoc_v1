## Get Customer Data

```http
GET /api/v1/customer/customer_number/account HTTP/1.1
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

    "billing_data": "none",
    "billing_data": {
      "gender":          "female",
      "title":           "",
      "first_name":      "Maxi",
      "last_name":       "Mustermann",
      "company":         "",
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
Before the function request, the <a href= "#customer-authentication"> customer must be authenticated</a>.
</aside>


### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.  

### Response
Parameter | Description
----------|-------------
**billing_data** | If no billing address and/or payment method given, the return value is zero.
**payment_data** | Specific data requested according to the method chosen.
**payment_data_logos** | Logos of the different types of payment methods: <ul> <div style="text-align: left;"> <li>Visa</li> <li>Master Card</li> <li>American Express</li> <li> PayPal</li> </ul>
**payment_data_types** | Different types of billing request different payment data.
