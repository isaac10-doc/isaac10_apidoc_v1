## getProducts - Retrieving of Product and Plan Data

```http
GET /api/v1/products HTTP/1.1
```

```javascript
isaac10.getProducts();
```

> Response

```json
{
  "products": [
    {
      "product_name 1": {
        "plans": [
          {
            "plan_name 1": {
              "nid": "NID Tarif 1",
              "price": [
                {
                  "interval": "monthly",
                  "cents": 0
                },
                {
                  "interval": "quarterly",
                  "cents": 0
                },
                {
                  "interval": "yearly",
                  "cents": 0
                }
              ],
              "setup_fee": null,
              "data": ""
            }
          },
          {
            "plan_name 2": {
              "nid": "NID Tarif 2",
              "price": [],
              "setup_fee": null,
              "data": null
            }
          },
          {
            "plan_name 3": {
              "nid": "NID Tarif 3",
              "price": [
                {
                  "interval": "monthly",
                  "cents": 2000
                }
              ],
              "setup_fee": 500,
              "data": null
            }
          }
        ]
      }
    },
    {
      "product_name 2": {
      }
    }
  ]
}
```


This function can be used to display project data on websites. If there's no products set on the subdomain, an empty array with status 200 will be returned.
