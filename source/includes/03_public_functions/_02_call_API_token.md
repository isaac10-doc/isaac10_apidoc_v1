## Call API Token of external Payment Service Providers


```http
GET /api/v1/api_token HTTP/1.1
```

```javascript
console.log(isaac10.apiToken);
// => { "notLoaded": true }

isaac10.withApiToken().then(function() {
  console.log(isaac10.apiToken);
  // => {
  //      "sandbox_mode":          true,
  //      "betterpayment_api_key": "123abc",
  //    }
});
```
> Response

```json
{
  "api_token": {
     "sandbox_mode":          "true",
     "betterpayment_api_key": "123abc"
   }
 }
```

To be able to use external payment service providers (PSPs) within the system, you need to configure your merchant account by displaying their public API tokens. Those public API tokens can be called by this request.

<aside class="notice">
This function is integrated in the JavaScript API. If an external API token for a function is required, he will automatically be called.   
<br>
<br>
    <strong>Using the JavaScript library, you never need to retrieve explicitly this external API token.</strong>  
  To retrieve it anyway, see JavaScript tab.
</aside>
