## Merchant Authentication




```javascript
isaac10.authenticateMerchant('merchant_token');

console.log(isaac10.merchantToken);  
// => "merchant_token"  
```


In order to use the merchant's functions you have to authenticate with the system using your merchant API token. To find your merchant API token, see the merchant backend under the following section:

**Konfiguration > Allgemeine Einstellungen**


### REST API
If a request requires the authentication of the merchant, the merchant's API token has to be transferred within the `Authorize` header.

`Authorization: Token token="<merchant_token>"`


### JavaScript API
When using the JavaScript API you have to authenticate yourself _before_ your first request of a protected function by using your merchant API token. The authentication itself works by the method `authenticateMerchant()` with an instance of the isaac10 object:


As mentionned above the request `authenticateMerchant()` _won't_ create a HTTP request. The merchant's API token gets stored in the _isaac10_ object and returned (if necessary) with every request.

He will be set as property as well and can be displayed with the _isaac10_ object:




<aside class="notice">
Both methods of authentication can be operated independently one of another. Both, customer and merchant API token can be set at the same time.
</aside>
