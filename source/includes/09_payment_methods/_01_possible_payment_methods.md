## Possible Payment Methods

isaac10 supports the following payment methods:

* on [invoice](#invoice)
* [direct debit (SEPA)](#direct-debit-sepa)
* [credit card](#credit-card)
* [PayPal](#paypal)

The parameter `payment_method` specifies, which payment method gets stored. Each payment method requires different additional parameter.

Depending on the payment method chosen, the output also differs in `payment_data` when calling the customer's data.
