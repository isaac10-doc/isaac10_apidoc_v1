## Invoice

> Parameters for request body
> _(full request body depends on request)_

```json
{
  "payment_method": "invoice"
}
```

For payment upon invoicing no further specifications are necessary.

> Response values for payment data
> _(full response depends on request)_

```json
{
  "payment_data": {
    "payment_method": "invoice"
  }
}
```

### Integration with JavaScript library

As payment on invoice doesn't require further specifications, transferring the value `invoice` is sufficient.
