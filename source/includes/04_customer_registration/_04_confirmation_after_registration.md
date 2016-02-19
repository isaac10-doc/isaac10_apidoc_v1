## Confirmation after Registration

```http
POST /api/v1/customer/customer_nmber/thank_you/subscription_id/register HTTP/1.1
```

```javascript
isaac10.thankYouAfterRegister(subscription_id, params);
```

> Request body / Params

```json
{"double_opt_in": true}
```

> Response

```json
{
  "plan": {

  },
  "subscription": {
    "id": "42",
    "begins_at": "2015-08-19",
    "term_ends_at": "2015-09-18",
    "billing_interval": "monthly",
    "next_billing_interval": "monthly",
    "status": "ongoing",
    "additions": []
  }
}
```

<aside class="success">
Before the function request, the <a href= "#customer-authentication"> customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|------------
**customer_number** | Number identifying the customer.
**subscription_id** | ID identifying the booking.


<aside class="notice">
Using this function, the transmission of the email informing the merchant about a new customer/new subscription as well as of the subscription confirmation email for the customer gets initiated. Therefore by using the <code>double-opt-in</code> it must be decided, whether an email for the customer is sent out or not.
</aside>


Every of the following functions [register - Customer registration](#register), [Adding a new Subscription](#adding-a-new-subscription) and [Upgrading/Downgrading](#upgrading-downgrading-a-subscription) create a new data record for a subscription, not yet been confirmed. The ID of this booking created will be used within the `thank you` functions, in order to confirm the newly created record. Consequently those functions aren't optional.
All kind of emails for new registrations, double-opt-in and Downgrade confirmations will also be initiated by the `thank you` functions.

### Response

Parameter | Description
----------|------------
**plan** | This data is the same as returned when calling `.getPlan()`
