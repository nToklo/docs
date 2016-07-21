![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)
#Events

The Events API allows customers to send nToklo user activity.

##REST template

| URI         | /event      |
|-------------|-------------|
| HTTP method | POST        |
|Request body | [UV](http://docs.qubitproducts.com/uv/intro/) object | 


##Example HTTP request
Note: some headers are omitted for brevity

```
POST /event
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:42ca49427aaf5d436dd906649887ca5c0bba0f0e
Content-Type: application/json; charset=utf-8
{
  "user": {"user_id": "112"},
  "product": {"id": "10201", "category": "Shoes", "manufacturer": "Nike"},
  "events": [{"name": "purchase"}]
}

HTTP/1.1 204 No Content
Content-Type: application/json; charset=utf-8
Content-Length: 0
```