## Set customer custom data

```http
PATCH /api/v1/customers/<customer_number>/custom_data HTTP/1.1
```

```javascript
isaac10.setCustomerCustomData(customer_number, data);
```

> Request body / Data

```text
Whatever you want. Please use responsibly, this is not a challenge.
```

> Response

```json
{
  "success": true
}
```

You may set custom data for any of your customers. The data can be anything, there are no validations. It will be stored as-is in the database. To read the data see [Get customer custom data](#get-customer-custom-data).

<aside class="success">
Before making the function call, you must <a href="#merchant-authentication">authenticate yourself</a>.
</aside>
