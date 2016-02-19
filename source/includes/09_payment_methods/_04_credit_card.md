## Credit Card

For the payment upon credit card _isaac10_ offers two different methods:

-   _isaac10_'s own integration: `"payment_method": "cc_betterpayment"`. This is a white label solution provided by [Better Payment](http://betterpayment.de/)
-   Micropayment integration: `"payment_method": "cc_micropayment"`.

<aside class="warning">
<strong> Payment upon Credit Card with Micropayment is not yet implemented</strong><br>
This documentation is ahead of its time. The payment method <code>cc_micropayment</code> is scheduled for delivery in the next release.
</aside>

A transfer of credit card information with the REST API is not possible for legal reasons. Credit card numbers _must never_ be transferred to your or our servers. Therefore only a client side integration through an iframe, directly provided by the payment provider, is a possible solution. However, in case you did the client side integration of the iframe yourself, the returned tokens can be transferred to _isaac10_ through the REST API.

### Request body for REST integration: `cc_betterpayment`

> Parameters for request body when Better Payment is used<br>
> _(full request body depends on request)_

```json
{
  "payment_method": "cc_betterpayment",
  "transaction_id": "transaction-ID of Better Payment"
}
```

To identify a payment transaction, Better Payment uses a `transaction_id`. Also the transfer of credit card information without immediate processing of a payment transaction (method used by _isaac10_) is treated in the same way. After a successful transfer of credit card information to Better Payment, the `transaction_id` can be sent over to _isaac10_.

### Response: `cc_betterpayment`

> Response values for payment data when Better Payment is used<br>
> _(full response depends on request)_

```json
{
  "payment_data": {
    "payment_method": "cc_betterpayment",
    "expire_month": "03",
    "expire_year": "15",
    "card_last4": "1234"
  }
}
```

Parameter | Description
----------|------------
**expire_month** and **expire_year** | The expiry date of the credit card.
**card_last4** | The last four digits of the credit card number.

### Request body for REST integration: `cc_micropayment`

> Parameters for request body when Micropayment is used
> _(full request body depends on request)_

```json
TODO
```

TODO

### Response: `cc_micropayment`

> Response values for payment data when Micropayment is used
> _(full response depends on request)_

```json
TODO
```

TODO

### Integration with JavaScript library

> Integration Example for JavaScript

```html
<!DOCTYPE html>
<html>
  <head>
    <script type="text/javascript">
      $(function() {
        function registerParams() {
          var params = {
            email: $('#email').val();
            /* all further data */
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

        /* when payment with credit card is choosen: display iframe */
        $('#payment_method_cc_betterpayment').on('change', function() {
          if ($('#payment_method_cc_betterpayment:checked')) {
            isaac10.displayCreditCardiframe('#credit-card-iframe', 400, 300);
          }
        });

        /* when "Place Order" is clicked: send values to payment provider and
           isaac10 */
        $('#register-form').submit(function(event) {
          event.preventDefault();
          isaac10.register({register: registerParams()});
        });
      });
    </script>
  </head>
  <body>
    <h1>Register</h1>

    <!-- register file -->
    <form id="register-form">
    <input type="text" name="email" id="email" />
      <!-- ...and all further information requested -->

      <!-- radio buttons for choosing payment method -->
      <label for="payment_method_elv_micropayment">
        SEPA
        <input type="radio"
               name="payment_method"
               value="elv_micropayment"
               id="payment_method_elv_micropayment" />
      </label>
      <label for="payment_method_cc_betterpayment">
        credit card
        <input type="radio"
               name="payment_method"
               value="cc_betterpayment"
               id="payment_method_cc_betterpayment" />
      </label>

      <!-- iframe to transfer credit card data -->
      <div id="credit-card-iframe"></div>

      <!-- submit button for registration -->
      <button>Place Order</button>
    </form>
  </body>
</html>
```

The JavaScript library (in comparison to an own implementation) offers an easy integration into your frontend. The procedure is the same for both, `elv_betterpayment` and `elv_micropayment`. Implementation procedure is as follows:

**1. Place a `<div>` in the HTML code**

where the iframe for the credit card form should be placed into.

**2. Display the credit card iframe**

by calling the function `isaac10.displayCreditCardiframe(selector, width, height)`. The call and therefore the display can be linked to a JavaScript event, e.g. chosing a radio button.

-   **selector** is the jQuery selector for the `<div>`, where the iframe shall be rendered
-   **width** and **height** are the dimensions of the iframe

**3. Transmit the credit card data**

by calling one of the functions that transmit payment data to _isaac10_ (e.g. registration of a new customer with `isaac10.register(...)` or updating of payment data `isaac10.updatePaymentData(...)`). Pass `"payment_method": "cc_betterpayment"` or `"payment_method": "cc_micropayment"` as payment method in the params hash _without any additional data_. This can be linked to a JavaScript event too, e.g. clicking a button `Place Order`.

The JavaScript library identifies the payment method and understands that the iframe got loaded and the customer entered his payment data in the iframe. The transmission of the data to Better Payment/Micropayment and the processing of the return values is done internally in the library. Then the transmission of the payment data (and all further information, depending on the called function) to _isaac10_ will be executed.

The example on the right shows the use of the JavaScript library to build a registration page. Please note that it is only complete for credit card payment. There is a radio button for SEPA payment but the necessary text fields for IBAN and account holder are missing. We will provide a complete example soon.
