![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)

# Blacklist

The Blacklist API allows customers to exclude items from being recommended and appearing in new charts.

##REST template

| URI	| /product/blacklist |
|--------|--------------------|
|Request method	 | POST, DELETE |

## Request parameters

| Name	 | Description	 | Examples |
| `productId` |	The unique identifier for the product which will added/removed from the blacklist. The productId can be any string value. In order to add/remove products in batches the productId can be specified multiple times. |	`10201, prod8513` |

## Example HTTP request
Note: some headers are omitted for brevity

### Add to blacklist

```
POST /product/blacklist?productId=10201&productId=42518
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:99fc1f3d2efed169246cce9e84369b6dcc9f6ff5
```
```
HTTP/1.1 204 No Content
Content-Type: application/json; charset=utf-8
Content-Length: 0
```

### Remove from blacklist

```
DELETE /product/blacklist?productId=10201&productId=42518
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:d8d6e3fdc0cf9848454468f0b0487b29a2eaecc2
```
```
HTTP/1.1 204 No Content
Content-Type: application/json; charset=utf-8
Content-Length: 0
```