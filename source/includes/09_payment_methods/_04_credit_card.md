## Credit Card

> Request body / Params
>
> - Better Payment

```json
{
  "payment_method": "cc_betterpayment",
  "transaction_id": "transaction-ID of Better Payment"
}
```

> Response
>
> - Better Payment

```json
{
  "payment_method": "cc_betterpayment",
  "expire_month": "03",
  "expire_year": "15",
  "card_last4": "letzte 4 Ziffern der Kartennummer"
}
```

> Integration - Example

> - HTML

```html
 <!-- register file -->  
<form id="register-form">
<input type="text" name="email" id="email" />
  <!-- ...and all further information requested -->

  <!-- radio buttons for choosing payment method -->
  <label for="payment_method_elv_micropayment">
    SEPA
    <input type="radio" name="payment_method" value="elv_micropayment" id="payment_method_elv_micropayment" />
  </label>
  <label for="payment_method_cc_betterpayment">
    credit card
    <input type="radio" name="payment_method" value="cc_betterpayment" id="payment_method_cc_betterpayment" />
  </label>

  <!-- iframe to transfer credit card data -->
  <div id="credit-card-iframe"></div>

  <!-- submit button for registration -->
  <button>Place Order</button>
</form>
```

> - JavaScript

```javascript
$(function() {
  function registerParams() {
    var params = {
      email: $('#email').val();
      /* all further information */
    };

    if ($('#payment_method_elv_micropayment:checked')) {
      $.extend(params, { payment_method: 'elv_micropayment',
                         account_holder: 'read value',
                         iban:           'read value' });
    } else if ($('payment_method_cc_betterpayment:checked')) {
      $.extend(params, { payment_method: 'cc_betterpayment' });
    }

    return params;
  }

  /*  initialize isaac10 library */
  var isaac10 = new Isaac10('my-subdomain');

  /* Wenn Zahlungs auf Kreditkarte ausgewählt wird: Zeige iframe an */
  $('#payment_method_cc_betterpayment').on('change', function() {
    if ($('#payment_method_cc_betterpayment:checked')) {
      isaac10.displayCreditCardiframe('#credit-card-iframe', 400, 300);
    }
  });

  /* when clicked "Place Order": sends values to isaac10 */
  $('#register-form').submit(function(event) {
    event.preventDefault();
    isaac10.register({register: registerParams()});
  });
});
```


For the payment upon credit card _isaac10_ offers two different methods:

* special interface of _isaac10_: `"payment_method": "cc_betterpayment"`. This is a white label solution provided by [Better Payment](http://betterpayment.de/)
* integration of Micropayment: `"payment_method": "cc_micropayment"`.

<aside class="warning">
<strong> Payment upon Credit Card with Micropayment is not yet implemented</strong><br>
This documentation is ahead of its time. The payment method <code>cc_micropayment</code> is scheduled for delivery in the next release.
</aside>

A transfer of credit card information with the REST API is not possible for legal reasons. Credit card number must _never_ be transferred to your or our servers. Therefore only a client side integration through an iframe, directly provided by the payment provider, is a possible solution. In case you did the client side integration yourself, the returned tokens can be transferred to _isaac10_ through the REST API. Another more simple possibility offers the JavaScript library.

### Params
#### CC_BETTERPAYMENT

To identify a payment transaction, Better Payment uses a `transaction_id`. Also the transfer of credit card information without immediate processing of a payment transaction (method used by _isaac10_) is treated in the same way. After a successful transfer of credit card information to Better Payment, the `transaction_id` can be sent over to _isaac10_.

#### CC_MICROPAYMENT
TODO

### Integration with JavaScript library

The JavaScript library (in compairison to an own implementation) offers an easy integration into your frontend. The procedure is the same for both, elv_betterpayment and elv_micropayment. Implementation procedure is as follows:  

1. In the HTML code place a <div>, where the iframe shall display the credit card entry.  
2. Call the function `isaac10.displayCreditCardiframe(selector, width, height)` to display the iframe. The call and therefore the display can be linked to a JavaScript Event, e.g. the choice of a radio
 button.
 * **selector** is the jQuery selector for ´<div>´, where the iframe shall be rendered
 * **width** and **height** is width and height of the iframe
3. Call one of those functions, transmitting payment data to _isaac10_ (e.g. registration of a new customer with `isaac10.register(...)` or updating of payment data `isaac10.updatePaymentData(...)`) and transfer `"payment_method": "cc_betterpayment"` or `"payment_method": "cc_micropayment"` as payment method without any additional information. This can be linked again to a JavaScript event, e.g. a click on the button `"Place Order"`.

The JavaScript library identifies automatically the payment method and understands that the iframe got loaded and the customer entered his payment data in the iframe. The transmission of the data to Better Payment/Micropayment and the processing of the return values is done internally in the library. Then the transmission of the payment data (and all further information, depending on the called function) to _isaac10_ will be executed.  
