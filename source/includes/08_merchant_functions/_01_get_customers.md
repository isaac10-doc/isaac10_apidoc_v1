## List all customers

```http
GET /api/v1/customers HTTP/1.1
```

```javascript
isaac10.getCustomers();
```

> Response

```json
{
  "customers": [
    {
      "account": {
        ...
      },
      "subscriptions": {
        ...
      }
    }
  ]
}
```

<aside class="success">
Before making the function call, you must <a href="#merchant-authentication">authenticate yourself</a>.
</aside>

### Response

Parameter | Description
----------|------------
**customers** | An array of all customers of the merchant.
**account** | The account data of the customer including billing address and payment data. See [Get Customer Account Data](#get-customer-account-data).
**subscriptions** | All subscriptions of the customer. See [List Customer Subscriptions](#list-customer-subscriptions).
