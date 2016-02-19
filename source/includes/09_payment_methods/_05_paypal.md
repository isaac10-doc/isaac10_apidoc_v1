## PayPal


> Request body / Params

```json
{
  "payment_method": "paypal"
}
```

> Response

```json
{
  "payment_method": "paypal"
}
```

### Params

For the payment with PayPal no further information need to be given. The system expects that after the transmission PayPal will be called and the billing agreement ID is sent to _isaac10_ as described in [Confirmation after Registration](#confirmation-after-registration).

### Setup

The input mask for your PayPal ID (normally your email address with PayPal) and the display of given agreements on behalf of PayPal, as far as this payment method is activated for you, can be found in

**Configuration > Payment methods**

<aside class="notice">
To be able to use the checkout express, place billing agreements for recurring payment in order and charge your customers on your behalf, you need to grant us the appropriate permissions. By clicking on "Set Permission" you'll be forwarded to the PayPal Merchant Domain, where you can grant the appropriate permissions. Afterwards you'll be backwarded to your _isaac10_ merchant backend again.
 </aside>


### Integration with JavaScript library

With our _isaac10_ JavaScript library you can call up the [In-Context-Express-Checkout](https://developer.paypal.com/docs/classic/express-checkout/in-context/) by what Paypal customers conclude a billing agreement with the merchant.
This billing agreement will be maintained in the background by _isaac10_ in order to use it for further debiting.

Please follow these steps:
<ol>
  <li> Call up the function which transfers the payment data (e.g. isaac10.register(…) or isaac10.updatePaymentData(…).   </li>

  <li> In case of registration: Authenticate the customer by using the data received in step 1. If you changed the payment data of an existing customer the authentication is already realized.  </li>

  <li> Call up the function isaac10.processPaypal('successURL', 'failureURL‘). After that you receive the express-chckeout-window by Paypal which redirects to Paypal.  </li>

    <ul>
      <li> successURL: Paypal redirects to this URL (\*\) in case the customer confirms the payment via Paypal. </li>
      <li> failureURL: Paypal redirects to this URL (\*\) in case the customer cancels the payment via Paypal. </li>
    </ul>
</ol>

(\*\) In deed, PayPal will lead back to _isaac10_, where the PayPal returned data get processed and linked to the customer. The final redirect to your page (to the passed `successURL` or `failureURL`) is done by _isaac10_.
