## PayPal

> Parameters for request body<br>
> _(full request body depends on request)_

```json
{
  "payment_method": "paypal"
}
```

> Response values for payment data<br>
> _(full response depends on request)_

```json
{
  "payment_data": {
    "payment_method": "paypal"
  }
}
```

### Params

For the payment with PayPal no further parameters (aside from `"payment_method": "paypal"`) need to be passed.

However, when using the REST integration, you must pass special `successURL`s and `failureURL`s to the PayPal API to make PayPal send the billing agreement back to _issac10_ and not directly to your website. (Description TODO)

When using the JavaScript library, the billing agreement of PayPal is sent to _isaac10_ automatically. This is described below.

### Setup in Merchant Configuration

The input mask for your PayPal ID (normally your email address with PayPal) and the display of given agreements on behalf of PayPal, as far as this payment method is activated for you, can be found in

**Settings > Payment methods**

<aside class="notice">
To be able to use the checkout express, place billing agreements for recurring payment in order and charge your customers on your behalf. You need to grant us the appropriate permissions. By clicking on "Set Permission" you'll be forwarded to the PayPal Merchant Domain, where you can grant the appropriate permissions. Afterwards you'll be backwarded to your _isaac10_ merchant backend again.
</aside>

### Integration with JavaScript library

With our _isaac10_ JavaScript library you can call up the [In-Context-Express-Checkout](https://developer.paypal.com/docs/classic/express-checkout/in-context/) by what PayPal customers conclude a billing agreement with the merchant.
This billing agreement will be maintained in the background by _isaac10_ in order to use it for further debiting.

Please follow these steps:

**1. Call a function which transfers the payment data**

e.g. `.register()` or `.updatePaymentData()` and pass `"payment_method": "paypal"` in the params.

**2. In case of registration: Authenticate the customer**

by using the customer number and customer token received by step 1. This is unnecessary if you changed the payment data of an existing customer. The authentication must have been already done in this case (otherwise you could not have called the function for changing the payment data in the first place).

**3. Call the function to process PayPal**

which is named `.processPaypal(successURL, failureURL)`.

-   **successURL:** PayPal redirects to this URL (\*) in case the customer confirms the payment via PayPal.
-   **failureURL:** PayPal redirects to this URL (\*) in case the customer cancels the payment via PayPal.

After the call the express checkout window by PayPal will open which redirects the customer to PayPal.

(\*) Indeed, we make PayPal to redirect back to _isaac10_, where the data returned by PayPal gets processed. The final redirect to your website (to the passed `successURL` or `failureURL`) is then done by _isaac10_ itself.
