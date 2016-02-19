## Registration Page for new Customers

### URL anchor
\#/plan/plan_nid

### Params

Parameter | Description
----------|-------------
**plan_nid** | The NID of the plan.


### Transfer Data to your System

Please go to your merchant-backend

**Settings > Integration settings**

This area offers you options to modify the register webhooks. You can chose a HTTP method (GET/POST) and enter an URL. By completing a new registration successfully the data will be transferred to the configured URL using the chosen HTTP-method.

Please file the values of `customer_number` und `customer_api_token` in your system. They are needed to [authenticate the customer](#customer-authentication) and therefore to display the overview pages.
