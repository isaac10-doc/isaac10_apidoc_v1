## Confirmation after Registration

```http
GET /api/v1/customer/<customer_nmber>/thank_you/<subscription_id>/register?double_opt_in=true HTTP/1.1
```

```javascript
isaac10.thankYouAfterRegister(subscription_id, { double_opt_in: true });
```

> Response

```json
{
  "plan": {
    ...
  },
  "subscription": {
    "id": "42",
    "product_name": "name of the product",
    "internal_product_name": "internal name of the product",
    "plan_name": "name of the plan",
    "begins_at": "2015-08-19",
    "term_ends_at": "2015-09-18",
    "billing_interval": "monthly",
    "next_billing_interval": "monthly",
    "status": "ongoing",
    "currency": "EUR",
    "price": [
      { "interval": "monthly", "cents": 1000 },
      { "interval": "quarterly", "cents": 3000 },
      { "interval": "yearly", "cents": 12000 }
    ],
    "additions": [
      ...
    ]
  }
}
```

<aside class="success">
Before making the function call, the <a href="#customer-authentication">customer must be authenticated</a>.
</aside>

### Params

Parameter | Description
----------|------------
**customer_number** (REST only) | Number identifying the customer.
**subscription_id** | ID of the subscription.
**double_opt_in** | Should a mail with a confirmation link be sent to the customer? `true` or `false` (optional, default: `true`)

<aside class="notice">
Using this function, the transmission of the email informing the merchant about a new customer/new subscription as well as of the subscription confirmation email for the customer gets initiated. Therefore by using the <code>double_opt_in</code> it must be decided, whether an email for the customer is sent out or not.
</aside>

Every of the following functions [register - Customer registration](#register), [Adding a new Subscription](#adding-a-new-subscription) and [Upgrading/Downgrading](#upgrading-downgrading-a-subscription) create a new data record for a subscription, not yet been confirmed. The ID of this subscription created will be used within the "thank you" functions, in order to confirm the newly created record. Consequently calling the "thank you" functions isn't optional.

All kind of emails for new registrations, double-opt-in and downgrade confirmations will also be initiated by the "thank you" functions.

### Response

Parameter | Description
----------|------------
**plan** | This data is the same as returned by [Request Plan Data](#request-plan-data)
**subscription** | The confirmed subscription.
**subscription.product_name** | The name of the product.
**subscription.internal_product_name** | The internal name of the product.
**subscription.plan_name** | The name of the plan.
**subscription.begins_at** | The date when the subscription started. Since this is the response for a new registration, it will be today.
**subscription.term_ends_at** | The date when this term (= the first term) ends.
**subscription.billing_interval** | The chosen billing interval.
**subscription.next_billing_interval** | The billing interval after this term ends. Since this is the response for a new registration, it will be the same as the billing interval.
**subscription.status** | See [List Customer Subscriptions](#list-customer-subscriptions). Since this is the response for a new registration, it will be `ongoing`.
**subscription.currency** | The currency.
**subscription.price** | The prices for the possible billing intervals.
**additions** | The subscribed additions.
