## List bill clearance

```http
GET /api/v1/bills HTTP/1.1
```

```javascript
isaac10.getClearance();
```

> Response

```json
{
  "bills": [
    {
      "id":                      123,
      "product_name":           "name of the product",
      "customer_number":        "100001",
      "currency":               "EUR",
      "brutto_amount":           11900,
      "netto_amount":            10000,
      "vat_amount":               1190,

      "bill_items": [
        {
          "invoice_text":       "the text appearing on the PDF invoice document",
          "brutto_base_amount":  4760,
          "netto_base_amount":   4000,
          "vat_base_amount":      760,
          "brutto_amount":       9520,
          "netto_amount":        8000,
          "vat_amount":          1520,
          "quantity":               2,
          "billed_from":        "2016-03-17",
          "billed_to":          "2016-04-16"
        },
        ...
      ]
    },
    ...
  ]
}
```

List all bills in the system that are not cleared. These appear in **Bills > Clearance** (german: **Rechnungen > Rechnungsfreigabe**) in the merchant backend. Please note that these bills do not have a bill number. The bill number is generated when a bill get's cleared.

<aside class="success">
Before making the function call, you must <a href="#merchant-authentication">authenticate yourself</a>.
</aside>
