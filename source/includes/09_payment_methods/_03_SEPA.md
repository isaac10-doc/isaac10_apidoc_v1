## Direct Debit (SEPA)

For the payment upon direct debit (SEPA) _isaac10_ offers two different methods:

-   integration of Micropayment: `"payment_method": "elv_micropayment"`
-   creation of SEPA-XML files, which you can deposit yourself at the bank: `"payment_method": "elv_dtaus"`. This method is traditionally known as "garage clearing".

> Parameters for request body / params when Micropayment is used<br>
> _(full request body / params depend on request)_

```json
{
  "payment_method": "elv_micropayment",
  "account_holder": "name of account holder",
  "iban": "the IBAN"
}
```

> Response values for payment data when Micropayment is used<br>
> _(full response depends on request)_

```json
{
  "payment_data": {
    "payment_method": "elv_micropayment",
    "account_holder": "name of account holder",
    "iban": "the IBAN"
  }
}
```

> Parameters for request body / params when garage clearing is used<br>
> _(full request body / params depend on request)_

```json
{
  "payment_method": "elv_dtaus",
  "addr_name": "name of account holder",
  "bank_iban": "the IBAN"
}
```

> Response values for payment data when garage clearing is used<br>
> _(full response depends on request)_

```json
{
  "payment_data": {
    "payment_method": "elv_dtaus",
    "account_holder": "name of account holder",
    "iban": "the IBAN"
  }
}
```

### Params

Parameter | Description
----------|-------------
**account_holder** or **addr_name**  | <ul> <li>required </li>  </ul>
**iban** or **bank_iban** | <ul> <li>required </li> <li>must be an existing IBAN </li>  </ul>

### Integration with JavaScript library

Account holder and IBAN can be called directly and be transferred to the respective JavaScript function. The transfer to Micropayment (elv_micropayment) will be made by _isaac10_ on the server side. Regarding SEPA-XML files (elv_dtaus), data will be stored by _isaac10_ itself.
