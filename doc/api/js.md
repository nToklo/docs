![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)

## POST-ing events via nToklo.js

The easiest and most common to way record your store’s activity is by leveraging the nToklo.js script.

In the example below we have a page that contains a `universal_variable` object. In order for nToklo to record the activity you must include the nToklo.js file in your page after the `universal_variable` object is assigned, being sure to also specify your **API key**:

```javascript
<script type="text/javascript">
window.universal_variable = {
  "version": "1.2",
  "user": {
    "user_id": "nicole12@yahoo.com",
    "name": "Nicole Watts",
    "language": "en_GB"
  },
  "page": {
    "type": "product",
    "breadcrumb": ["Womens", "Shoes", "French Sole"]
  },
  "events": [
    {
      "category": "conversion_funnel",
      "action": "preview"
    }
  ],
  "product": {
    "id": "frenchsole_1021",
    "url": "http://www.fashionbay.com/womens/shoes/french_sole_flats_1021.html",
    "name": "French Sole: Classic Ballet",
    "unit_price": 65,
    "unit_sale_price": 65,
    "currency": "GBP",
    "description": "This beautifully soft, unstructured ballet flat is ...",
    "category": "shoes"
  }
}
var _ntoklo_key = "NTRjN2M4OWMtMzg1NS00YWNhLWJiODAtMzQzYjYwYWE3YzUx";
</script>

<script type="text/javascript" src="https://console.ntoklo.com/static/js/ntoklo.js"></script>
```

## Asynchronous events

Some events occur asynchronously, i.e. not on page load. A typical example is a rate, favourite, or like interaction. Such actions often involve clicking a button and updating the DOM asynchronously. In such cases you can send UV objects asynchronously by invoking `window.ntoklo.sendEvent`.

Here's an example:
```javascript
<script type="text/javascript" src="https://console.ntoklo.com/static/js/ntoklo.js"></script>
<script type="text/javascript">
  /* construct UV object representing the asynchronous event */
  var eventObject = {
    "events": [
      {
        "category": "conversion_funnel",
        "action": "rate"
      }
    ],
    "user": {
      "user_id": "8492834083"
    },
    "product": {
      "id": "ABC123",
      "manufacturer": "Acme Corp",
      "category": "Shoe"
    }
  }
 
  /* send the event, triggered by a click event or something similar */
  window.ntoklo.sendEvent(eventObject);
</script>
```

## Universal Variable (UV)

Not using UV object in your pages? Why not start leveraging the [Universal Variable open standard](http://docs.qubitproducts.com/uv/specification/).

If you are not using UV objects in your pages then you may still record activities via server-side API calls. Please read more about recording activities server-side with the [Events API](events.md).