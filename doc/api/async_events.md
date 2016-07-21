![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)
# Asynchronous events

Some events occur asynchronously, i.e. not on page load. A typical example is a rate, favourite, or like interaction. Such actions often involve clicking a button and updating the DOM asynchronously. In such cases you can send UV objects asynchronously by invoking window.ntoklo.sendEvent.

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
