![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)

# Recommendations

The Recommendations API allows customers to retrieve recommendations based on user history and product attributes. It may also provide popular products for non-personalised recommendations.

## URI template

| URI         | /event      |
|-------------|-------------|
| HTTP method | GET        |
|Request body | Recommendation object that contains an array of Product objects. | 


## Request parameters

| Name  	| Description	| Examples |
|-----------|---------------|----------|
| `userId`	| (*Optional*) Uniquely identifies the user for which the recommendations are intended. If the `userId` is not provided then the recommendations returned will not be personalised. The `userId` can be any value of string type.  |	`dan@gmail.com, 11245901, user_123` |
| `productId`	| (*Optional*) The product for which to base recommendations from. The `productId` can be any string value.	| `10201,prod8513`  |
| `scope`	    | (*Optional*) A product attribute for which to scope recommendations. For example `scope=category` will consider the product category when returning recommendations. Supports: `category, manufacturer, vendor, action`.	 | `category, manufacturer, vendor, action`  |
| `value`	    | (*Optional*) The value for the recommendation scope. For example `scope=category&value=shoes` will consider the shoe category when returning recommendations. The value parameter can be any string value. |	`shoes, category12, nike, shoes.com` |

## Example HTTP request
Note: some headers are omitted for brevity

```
GET /recommendation?userId=112&productId=10201
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:43f47bcfb5eb0485ef828cf16cb2a7e490a76069
```
```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
{
  "tracker_id": "2b169680-aa86-12e5-9c37-600308a4f234",
  "items": [
    {
      "id": "10242",
      "name": "Campbell capri in wave print",
      "currency": "GBP",
      "unit_sale_price": 98
    },
    {
      "id": "22832",
      "name": "Andie chino",
      "currency": "GBP",
      "unit_sale_price": 79.5
    },
    {
      "id": "12955",
      "name": "Collection cropped trouser in antique floral",
      "currency": "GBP",
      "unit_sale_price": 298
    }
  ]
}
```
