## updateBillingData - Updating the Customer's Billing Address

```http
PATCH /api/v1/cstomer/customer_number/account/billing_data HTTP/1.1
```

```javascript
isaac10.updateBillingData(params);
```

> Request body/ params

```json
{
  "billing_data": {
    "gender":          "female",
    "title":           "",
    "first_name":      "Vorname",
    "last_name":       "Nachname",
    "company":         "",
    "street":          "Musterstraße 1",
    "zip":             "12345",
    "city":            "Musterstadt",
    "ustid":           "DE1234567890"
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
**gender** | The gender of the customer. <ul> <div style="text-align: left;"> <li>required</li> <li>allowed values: `male`, `female`</li> </ul>
**first_name** | The first name of the customer. <ul> <div style="text-align: left;"> <li>required</li> </ul>
**last_name** | The last name of the customer. <ul> <div style="text-align: left;"> <li>required</li> </ul>
**street** | The street of the customer's billing address. <ul> <div style="text-align: left;"> <li>required</li> </ul>
**zip** | The zip code of the customer's billing address. <ul> <div style="text-align: left;"> <li>required</li> </ul>
**city** | The city of the customer's billing address. <ul> <div style="text-align: left;"> <li>required</li> </ul>
