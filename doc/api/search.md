# Search

The Search API allows clients to search products by keyword.

## URI template

| URI	| /search |
|-------|-----------|
| Request method |	GET |
| Response body	| List of Product objects. |

##Request parameters

| Name	 | Description	 | Examples |
|-------|-----------|-------|
| `q` |	A query string containing the search keyword. | `nike air max ` |
| `from` | 	(*Optional*) A pagination argument which specifies the index of the page in which to return. |	`0,3` |
| `size` | (*Optional*) A pagination argument which specifies the size of each page, i.e. the number of products on each page. | `10, 50` |

## Example HTTP request
Note: some headers are omitted for brevity

```
GET /search?q=bell
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:43f47bcfb5eb0485ef828cf16cb2a7e490a76069
```

```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
[
  {
    "id": "10242",
    "name": "Campbell capri in wave print",
    "currency": "GBP",
    "unit_sale_price": 98
  },
  {
    "id": "22832",
    "name": "Campbell capri",
    "currency": "GBP",
    "unit_sale_price": 79.5
  },
  {
    "id": "12955",
    "name": "Collection of bells",
    "currency": "GBP",
    "unit_sale_price": 298
  }
]
```
