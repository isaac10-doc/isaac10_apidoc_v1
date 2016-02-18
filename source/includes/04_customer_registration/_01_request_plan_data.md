## getPlan - Request Plan Data

```http
GET /api/v1/register/plan_nid HTTP/1.1
```

```javascript
isaac10.getPlan('plan_nid');
```

> Response

```json
{
  "plan": {
    "nid": "<plan_nid>",
    "product_name": "name of the product",
    "plan_name": "name of the plan",
    "public": true,
    "logo_url": "http://path/to/merchant/logo.png",

    "imprint_url_de": "http://example.com/imprint_de",
    "terms_of_use_url_de": "http://example.com/terms_of_use_de",
    "privacy_notice_url_de": "http://example.com/privacy_notice_de",
    "withdrawal_notice_url_de": "http://example.com/withdrawal_notice_de",
    "imprint_url_en": "http://example.com/imprint_en",
    "terms_of_use_url_en": "http://example.com/terms_of_use_en",
    "privacy_notice_url_en": "http://example.com/privacy_notice_en",
    "withdrawal_notice_url_en": "http://example.com/withdrawal_notice_en",

    "success_redirect_url": "",
    "instant_redirect": false,

    "pricing": "brutto",
    "price": [
      { "interval": "monthly", "cents": 1000 },
      { "interval": "quarterly", "cents": 3000 },
      { "interval": "yearly", "cents": 12000 }
    ],
    "setup_fee": 500,
    "currency": "EUR",

    "data": "Your API data you entered in the product configration",

    "always_ask_for_billing_and_payment_data": false,

    "vat_b2c": [
      { "country": "DE", "percent": "19.0" },
      { "country": "CH", "percent": "11.0" },
      { "country": "BE", "percent": "19.0" }
    ],

    "vat_b2c": [
      { "country": "DE", "percent": "19.0" },
      { "country": "CH", "percent": "11.0" },
      { "country": "BE", "percent": "19.0" }
    ],
    "merchant_country": "DE",

    "additions": [
      {
        "nid": "NID of addition 1",
        "name": "name of addition 1",
        "price": [
          { "interval": "monthly", "cents": 100 },
          { "interval": "quarterly", "cents": 300 },
          { "interval": "yearly", "cents": 1200 }
        ],
        "quantifiable": false
      },
      {
        "nid": "NID of addition 2",
        "name": "name of addition 2",
        "price": [
          { "interval": "monthly", "cents": 200 },
          { "interval": "quarterly", "cents": 600 },
          { "interval": "yearly", "cents": 2400 }
        ],
        "quantifiable": true
      }
    ],
    "payment_data_logos": ["visa", "mastercard"],
    "payment_data_types": ["invoice", "elv_dtaus"]
  }
}
```

Request the data necessary to display the registration form.

### Params

Parameter | Description
----------|-------------|------------
**plan_nid** (in URL) | The NID of the plan

### Response

<aside class="notice">
A description for all parameters will follow.
</aside>

Parameter | Description
----------|------------
**vat_b2b** | This key is only included when a B2B VAT list is assigned to the product of the plan.
