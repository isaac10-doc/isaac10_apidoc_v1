## API Integration

### REST API

The REST API can be used with any HTTP client. All API requests must use HTTPS
and need to be send to:

`https://your-subdomain.isaac10.com`

Replace `your-subdomain` with... well... your subdomain.

<aside class="notice">
All <code>PATCH</code> requests may also be called as <code>PUT</code>
requests. This does not change the functionality: Although <code>PUT</code>
is meant to be used for replacing an entity, only the submitted data will be
altered. Present and non-submitted data will stay in place.
</aside>

All REST API calls will respond with the JSON content described in the right
panel.

### JavaScript API

Load the JavaScript library into the page and initialize the `isaac10`
JavaScript object as shown on the right side.

`<script type="text/javascript" src="https://app.issac10.com/api/v1/isaac10_api.js"></script>`

```javascript
var isaac10 = new Isaac10("your-subdomain");
```

All API functions are called on this object and return a Promise which passes
the JSON response of the API call to `success` and `failure`.
