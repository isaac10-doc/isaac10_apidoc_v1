## Download of a PDF Bill

```http
GET /api/v1/customer/customer_number/bills/bill_slug/type_name HTTP/1.1
```

```javascript
isaac10.downloadBill(url);
```

> Response

```json
{
  "url": "https://..."
}
```


<aside class="success">
Before the function request, the <a href= "#customer-authentication"> customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.
**bill_slug** | Designation of the bill.
**type_name** | Type of the bill.

### REST API
The return value contains a temporary URL for the PDF file. It's validity is about one hour. A call of this temporary URL by a `get` request returns a bill as PDF file.

### JavaScript API

The call of the JavaScript function by calling the REST API creates a temporary URL. **Subsequently the bill as PDF file is downloading.** The temporary URL won't be returned.
