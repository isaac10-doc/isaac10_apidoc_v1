## Invoice

> Request body / Params

```json
{
  "payment_method": "invoice"
}
```

For payment upon invoicing no further specifications are necessary.

> Response

```json
{
  "payment_method": "invoice"
}
```

### Integration with JavaScript library
As payment upon invoice doesn't require further specifications, transferring the value `invoice` is sufficient.
