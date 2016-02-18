## getBills - Calling the Customer's Bills

```http
PATCH /api/v1/cstomer/customer_number/bills HTTP/1.1
```

```javascript
isaac10.getBills();
```

> Response

```json
{
  "bills":
    [
      [
        {
          "type_name": "bill_cancelation",
          "bill_number": "0001/2015/X",
          "canceled_at": "2015-08-19",
          "cents": 2000,
          "currency": "EUR",
          "url": "http://url/to/bill"
        },
        {
          "type_name": "bill",
          "bill_number": "0001/2015",
          "billed_at": "2015-08-14",
          "cents": 2000,
          "currency": "EUR",
          "url": "http://url/to/bill"
        },
        {
          "type_name": "first_dunning",
          "bill_number": "0001/2015/1",
          "billed_at": "2015-08-19",
          "cents": 2500,
          "currency": "EUR",
          "url": "http://url/to/bill"
        },
        {
          "type_name": "first_dunning_cancelation",
          "bill_number": "0001/2015/1/X",
          "canceled_at": "2015-08-19",
          "cents": 2500,
          "currency": "EUR",
          "url": "http://url/to/bill"
        }
      ]
    ]
}

```


<aside class="success">
Before the function request, the customer must be authenticated.
</aside>

### Params

Parameter | Description
----------|-------------
**customer_number** (in URL) | The number identifying the customer.
