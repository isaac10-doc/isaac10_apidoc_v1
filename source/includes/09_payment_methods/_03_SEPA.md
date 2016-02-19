## Direct Debit (SEPA)

For the payment upon direct debit (SEPA) _isaac10_ offers two different methods:

* integration of Micropayment: `"payment_method": "elv_micropayment"``
* creation of SEPA-XML files, which you can deposit yourself at the bank: `"payment_method": "elv_dtaus"`. This method is traditionally known as "garage cleaning".


> Request body / Params
>
> - elv_micropayment

```json
{
  "payment_method": "elv_micropayment",
  "account_holder": "Name des Kontoinhabers",
  "iban": "IBAN"
}
```

> - elv_dtaus

```json
{
  "payment_method": "elv_dtaus",
  "addr_name": "Name des Kontoinhabers",
  "bank_iban": "IBAN"
}
```

> Response
>
> - elv_micropayment

```json
{
  "payment_method": "elv_micropayment",
  "account_holder": "Name des Kontoinhabers",
  "iban": "IBAN"
}
```

> - elv_dtaus

```json
{
  "payment_method": "elv_dtaus",
  "addr_name": "Name des Kontoinhabers",
  "bank_iban": "IBAN"
}
```


### Validation

Parameter | Description
----------|-------------
**account_holder** or **addr_name**  | <ul> <li>required </li>  </ul>
**iban** or **bank_iban** | <ul> <li>required </li> <li>must be an existing IBAN </li>  </ul>

### Integration with JavaScript library
Account holder and IBAN can be called directly and be transferred to the respective JavaScript function. The transfer to Micropayment (elv_micropayment) will be made by _isaac10_ on the server side. Regarding SEPA-XML files (elv_dtaus), data will be stored by _isaac10_ itself.
