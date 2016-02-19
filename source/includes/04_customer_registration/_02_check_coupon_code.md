## checkCouponCode - Verification Coupon Code


```http
GET /api/v1/register/coupons/coupon_code?plan=plan_nid HTTP/1.1
```

```javascript
isaac10.checkCouponCode(coupon_code, {"plan_nid": "<plan_nid>" });
```

> Response

```json
{
 "coupon":
 {
   "coupon_code": "<coupon_code>",
   "cents": 1200,
   "message": "Erfolgsmeldung des Gutscheins"
 }
}
```

### Params

Parameter | Description
----------|------------
**coupon_code** | Code of the coupon
**plan_nid** | NID of the plan
