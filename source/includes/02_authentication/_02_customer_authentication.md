## Customer Authentication

For using the functions regarding customer specific data, the customer has to be authenticated. The data required for authentication of the customer (API token, customer number) after a register request are returned as `customer_token` and `customer_number` and have to be stored in your system.

If you wish to outsource the authentication process entirely to our _isaac10_ system, you need to embed the API call [authenticate - login of customer](#login), returning token and customer number.

### REST API

```http
GET /api/v1/... HTTP/1.1
Authorization: Token token="<customer_token>"
```

If a request requires the authentication of the customer, the customer's API token has to be sent within the `Authorization` Header. The customer number, as part of the URL, has to be transferred as well.

### JavaScript API

```javascript
isaac10.authenticateCustomer("<customer_number>", "<customer_token>");
```

When using the JavaScript API the customer has to be authenticated _before_ his first request of a protected function by using his customer number and his API token. The authentication itself works by the method `.authenticateCustomer()` with an instance of the isaac10 object. (shown right)

The request `authenticateCustomer()` itself _won't_ create a HTTP request. The client's customer number as well as the customer token gets stored in the _isaac10_ object and returned (if necessary) with every request.

```javascript
console.log(isaac10.customerNumber);
// => "<customer_number>"`

console.log(isaac10.customerApiToken);
// => "<customer_api_token>"`
```

Once customer number and API token of the customer set, they can be displayed as properties of the _isaac10_ object. (shown right)
