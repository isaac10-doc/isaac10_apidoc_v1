## Customer specific Pages


```javascript
isaac10.authenticateCustomer("<customer_number>", "<customer_token>");
```


To display the pages and forms involving account-, billing- and subscription-data the customer need to get authenticated via the JavaScript-API (see Javascript tab).


You receive the parameter `customer_number` and `customer_token` with the form on [Registration Page for new Customers](#registration-page-for-new-customers) (or alternatively by [Register a Customer via API](#register)).

### URL anchors

Called Page  | Anchor
-------------|-------------
account data | **#/account**
billing data | **#/bills**
subscription data | **#/subscriptions**
