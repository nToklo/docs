![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)
# Charts

The Charts API allows customers to retrieve a list of popular products. Charts represents a rolling time window (daily or weekly) and can be scoped by product attributes and filtered by action.

## REST template

| URI	|  /chart |
|-------|---------|
|HTTP method  |	GET |
| Response body	 | Chart object that contains an array of ChartItem objects.|

## Request parameters

| Name	 | Description	| Examples |
|-------|---------|---------|
| `date` | 	(*Optional*) The date for which to retrieve a chart. The date should be an epoch timestamp in milliseconds, truncated to midnight.|	`1364169600000` |
| `scope` |	(*Optional*) A product attribute for which to scope charts. For example `scope=category` will consider the product category when returning charts. Supports: `category, manufacturer, vendor`.	| `category, manufacturer, vendor` |
| `value` |	(*Optional*) The value for the recommendation scope. For example `scope=category&value=shoes` will consider the shoe category when returning charts. The value parameter can be any string value.	| `shoes, category12, nike, shoes.com` |
| `action` |	(*Optional*) Filters the requested chart by conversion_funnel actions. If it’s not specified then the chart returned is all actions, equivalent to `action=all`. | |	
| `tw` |	(*Optional*) The time window for which the charts are requested. If not specified then the chart returns daily chart, equivalent to tw=DAILY. Supports: `DAILY, WEEKLY`.	| `DAILY, WEEKLY` |
| `maxItems` |	(*Optional*) The max number of items in the charts. Default is `10`. Valid range is `1-100`.	| `10` |

## Example HTTP request
Note: some headers are omitted for brevity
```
GET /chart?scope=category&value=sci-fi&maxItems=3
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:501685abe09d09e95615bd38743a8a3a9a9213fd
```
```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
{
  "tracker_id": "d91a6a80-a181-12e5-9c37-600308a4f234",
  "items": [
    {
      "currentPosition": 1,
      "previousPosition": 2,
      "peakPosition": 1,
      "score": 58,
      "timesOnChart": 6,
      "product": { ... }
    },
    {
      "currentPosition": 2,
      "previousPosition": 1,
      "peakPosition": 1,
      "score": 45,
      "timesOnChart": 12,
      "product": { ... }
    },
   {
      "currentPosition": 3,
      "previousPosition": 0,
      "peakPosition": 3,
      "score": 39,
      "timesOnChart": 1,
      "product": { ... }
    }
  ]
}
```
