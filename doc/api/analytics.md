![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)
# Clickthrough Analytics

In order for nToklo to provide clickthrough and conversion analytics, you must include clickthrough events in the UV objects sent to nToklo servers.

This is an optional, and advanced feature; but the benefits are worth the effort to support it.

## 1. Impressions
The first step is to fetch a recommendation set. You will receive an array of recommended items as well as a `tracker_id`.

`GET /recommendation?productId=12014`

```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "tracker_id": "2b169680-aa86-12e5-9c37-600308a4f234",
  "items": [
    {
      "id": "10242",
      "name": "MOTO Frayed Daisy Hotpant",
      "currency": "GBP",
      "unit_sale_price": 22,
      ...
    },
    { ... }
  ]
}
```

Now you want to render the recommendation set on the page; let's say it's a product page. You want the `universal_variable` object to include the impression event with the `tracker_id`, so the UV object will look as follows:

```
{
  "version": "1.2",
  "events": [
    {
      "category": "conversion_funnel",
      "action": "preview"
    },
    {
      "category": "clickthrough_goals",
      "action": "recommendation-impr",
      "tracker_id": "2b169680-aa86-12e5-9c37-600308a4f234"
    }
  ],
  "product": {
    "id": "10772",
    "name": "Navy Folk Scarf Print Shorts",
    "currency": "GBP",
    "unit_sale_price": 32,
    ...
  },
  "user": {
    "user_id": "beth89"
  },
  "page": {
    "type": "product",
    "breadcrumb": ["Home", "Women", "Shorts"]
  }
}
```

Notice that the impression event is simply appended to the `events` array. Clickthrough events are indicated by the category clickthrough_goals. If you fetch a recommendation set, the corresponding action should be `recommendation-impr`. If you fetch a chart, the action should be `chart-impr`.

## 2. Clicks
The click event is just as simple to implement. When a user clicks on a recommended item, the tracker_id should be forwarded to the resulting page. It is up to you how to forward the tracker_id but it is typical to simply pass it through via request parameter, e.g.:

`http://fashionbay.com/product?id=10242&nt_tracker=2b169680-aa86-12e5-9c37-600308a4f234`

When the UV object renders on the resulting page, you want it to include the click event with the tracker_id. In this example we passed the tracker_id through via arbitrary request parameter. So the UV looks as follows:

```
{
  "version": "1.2",
  "events": [
    {
      "category": "conversion_funnel",
      "action": "preview"
    },
    {
      "category": "clickthrough_goals",
      "action": "recommendation-click",
      "tracker_id": "2b169680-aa86-12e5-9c37-600308a4f234"
    }
  ],
  "product": {
    "id": "10242",
    "name": "MOTO Frayed Daisy Hotpant",
    "currency": "GBP",
    "unit_sale_price": 22,
    ...
  },
  "user": {
    "user_id": "beth89"
  },
  "page": {
    "type": "product",
    "breadcrumb": ["Home", "Women", "Shorts"]
  }
}
```

Notice that the click event looks similar to the impression event, except the action is `recommendation-click`. Similarly, if you had fetched a chart the action would be `chart-click`.