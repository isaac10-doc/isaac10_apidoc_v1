## Clear bill

```http
PATCH /api/v1/clearance/<bill_id>
```

```javascript
isaac10.clearBill("bill_id");
```

> Response

```json
{
  "success": true
}
```

Clears the bill with the given ID.

<aside class="success">
Before making the function call, you must <a href="#merchant-authentication">authenticate yourself</a>.
</aside>

### Params

Parameter | Description
----------|------------
**bill_id** | The ID of the bill to clear. Retrieve it by calling [List Bill Clearance](#list-bill-clearance).
