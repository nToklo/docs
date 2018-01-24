![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)

# Products

The Products API allows you to update product information recorded by nToklo. The Recommendations API will return the last known product information.

## REST template

| URI	| /products |
|-------|---------------|
|HTTP method |	PUT, POST, GET |
|Request Body |	Product object (as from [UV specification](http://docs.qubitproducts.com/uv/specification/#product)) |

## Example HTTP request
Note: some headers are omitted for brevity

### Adding a new product

```
POST /products
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:42ca49427aaf5d436dd906649887ca5c0bba0f0e
Content-Type: application/json; charset=utf-8
{
  "id": "10201",
  "name": "Gabardine A-line skirt",
  "category": "Womens > Skirts",
  "currency": "GBP",
  "unit_sale_price": 98
}
```

```
HTTP/1.1 200 Ok
Content-Type: application/json; charset=utf-8
Content-Length: 0
```

### Get a product by ID:

```
GET /products/10242
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:42ca49427aaf5d436dd906649887ca5c0bba0f0e
```

```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
{
  "id": "10242",
  "name": "Campbell capri in wave print",
  "currency": "GBP",
  "unit_sale_price": 98
}
```
