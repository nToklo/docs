![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)

# Basic Integration

You should be familiar with the [Getting Started](doc/api/getting_started.md) first. In general there are three steps to basic integration with nToklo.

## 1. Implement the Universal Variable (UV)
The UV is an open standard for describing customer experience data, e.g. what interactions occur on which products, by who, on what page.

The UV is great! Read more about the UV spec [here](http://docs.qubitproducts.com/uv/specification/).

nToklo cares about the interactions on your site, thus a good starting point is to identify or define your “conversion funnel” actions. You can define your own conversion funnel, but the typical purchase funnel is: `browse -> preview -> wishlist -> purchase -> rate -> review`.

You purchase funnel actions should be set like so:

```javascript
{
  "events": [
    {
      "category": "conversion_funnel",
      "action": "purchase"
    }
  ]
}
```
**Note**: the category indicates that the event is a “conversion funnel” event.

Most interactions involve one product, and the user that performed the action. The following is an example of a preview interaction:

```javascript
{
  "version": "1.2",
  "events": [
    {
      "category": "conversion_funnel",
      "action": "preview"
    }
  ],
  "product": {
    "id": "J10613",
    "name": "NSF Beck Boyfriend Jean",
    "description": "Soho blue cotton 'Beck' boyfriend jeans from NSF featuring belt loops and five pocket design.",
    "image_url": "https://s1.fashionbay.com/image/J10613.png",
    "vendor": "Farfetch",
    "currency": "GBP",
    "unit_price": 275.9
  },
  "user": {
    "user_id": "sophie95"
  },
  "page": {
    "type": "product"
    "breadcrumb": ["Home", "Women", "Jean"]
  }
}
```

**Note**: nToklo adds a few extra properties that the UV does not currently support, e.g. `image_url` and `vendor`.

A purchase action looks like this:

```javascript
{
  "version": "1.2",
  "events": [
    {
      "category": "conversion_funnel",
      "action": "purchase"
    }
  ],
  "transaction": {
    "line_items": [
      {
        "product": {
          "id": "S90300",
          "name": "Neoprene Bailey Skater Skirt",
          "description": "Our Bailey Skater Skirt in modern neoprene fabric is the perfect wardrobe updater.",
          "image_url": "https://s1.fashionbay.com/image/S90300.png",
          "vendor": "Whistles",
          "currency": "GBP",
          "unit_price": 75,
          "unit_sale_price": 60
        },
        "quantity": 1
      },
      { ... }
    ],
    "subtotal": 115,
    "shipping_cost": 8,
    "tax": 14.76,
    "total": 137.76,
    "currency": "GBP"
  },
  "user":  {
    "user_id": "nikki7"
  },
  "page": {
    "type": "product",
    "breadcrumb": ["Home", "Women", "Skirt"]
  }
}
```

Some interactions involve multiple products, e.g. a `browse` action is represented like this, notice the `listing` object which contains an array of Product objects:

```javascript
{
  "version": "1.2",
  "events": [
    {
      "category": "conversion_funnel",
      "action": "browse"
    }
  ],
  "listing": {
    "items": [
      {
        "id": "A10001",
        "name": "Linen Popover in Stripe",
        "description": "What to wear when you don't have anything to wear. Linen. Long roll-up sleeves. Chest pocket.",
        "image_url": "https://s1.fashionbay.com/image/A10001.png",
        "vendor": "J. Crew",
        "currency": "GBP",
        "unit_sale_price": 71.55,
        "unit_price": 79.5
      },
      { ... }
    ]
  },
  "user": {
    "user_id": "claire_bear"
  },
  "page": {
    "type": "homepage"
  }
}
```

Notice that the browse event above is describing the homepage, which contains a list of products.

## 2. Send data to the nToklo servers
Sending data to nToklo is as simple as dropping the nToklo Javascript tag into each page containing a UV object.

```javascript
<script type="text/javascript">
  window.universal_variable = { ... };
  var _ntoklo_key = "NTRjN2M4OWMtMzg1NS00YWNhLWJiODAtMzQzYjYwYWE3YzUx";
</script>
<script type="text/javascript" src="https://console.ntoklo.com/static/js/ntoklo.js"></script>
```

For native mobile applications you can send data using the Events API directly. You should be familiar with request authentication when using the nToklo APIs directly.

## 3. Fetch recommendations
Once there is enough data, you can start to fetch recommendations – in most cases, a days worth of data is enough. The more data, the better the recommendations. Let's look at some examples:

- Let's fetch a recommendation set for people who have purchased the *Crepe Seam Flippy Dress (id=F25317)*:

`GET https://api.ntoklo.com/recommendation?productId=F25317&scope=action&value=purchase`

- I want recommendations to be personalised, i.e. show me products that would interest Sophie based on what she's purchased in the past, and don't show her products she's purchased already:

`GET https://api.ntoklo.com/recommendation?userId=sophie95&scope=action&value=purchase`

- I want to promote shoes; recommend only shoe products:

`GET https://api.ntoklo.com/recommendation?userId=sophie95&scope=category&value=shoes`

You can read about all the options in the [Recommendations API](recommendations.md).
