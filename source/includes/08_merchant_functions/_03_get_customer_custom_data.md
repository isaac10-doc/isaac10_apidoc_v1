## Get customer custom data

```http
GET /api/v1/customers/<customer_number>/custom_data HTTP/1.1
```

```javascript
isaac10.getCustomerCustomData(customer_number);
```

> Response

```text
Whatever you set at the customer. The content type "text/plain" is used.
```

Retrieve the data you set with [Set customer custom data](#set-customer-custom-data).

<aside class="success">
Before making the function call, you must <a href="#merchant-authentication">authenticate yourself</a>.
</aside>
