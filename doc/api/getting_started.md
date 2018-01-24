![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)

# Getting Started

The nToklo API will help you provide a personalised experience for your customers. Integrate your [Universal Variable](http://docs.qubitproducts.com/uv/intro/) objects with the Events API. Fetch product recommendations and charts. Improve your sales!

Let us walk you through the keys steps for creating your nToklo application and integrating with our core features.

## Step 1. Register an application
[Register with nToklo](http://console.ntoklo.com/register), and create an application. An “application” represents your store on the nToklo platform.

Provide your store’s name and web address, and submit your application. You are now ready to integrate your store with nToklo.

![Register with nToklo](https://cloud.githubusercontent.com/assets/1387097/17016906/20acf276-4f29-11e6-8ad7-b805a9c71873.gif)

In order to use nToklo APIs you need your API key, which you can find on your console.

> API information

> **Key**  YzlkNzdhNTctNjEzMC00YjllLTlhNWItYjc3ZDY3MjQwZjNi
>**Secret** Yzc3YTdhYjEtM2ViNS00ZmFiLWFkZDUtMGFhNjkzMDIzZmUw

## Step 2. Add the nToklo Javascript tag to your website
The [Universal Variable (UV)](http://docs.qubitproducts.com/uv/intro/) makes integration with nToklo easy. If you are already using the UV, and your product pages already contain universal_variable objects, then you can start sending user activity to the nToklo servers – it's easy, just add the [nToklo Javascript tag](/doc/api/js.md) to each page and specify your nToklo application key.

```javascript
<script type="text/javascript">
  window.universal_variable = {}; // put your universal_variable object here
  var _ntoklo_key = "NTRjN2M4OWMtMzg1NS00YWNhLWJiODAtMzQzYjYwYWE3YzUx";
</script>
<script type="text/javascript" src="https://console.ntoklo.com/static/js/ntoklo.js"></script>
```

The nToklo Javascript will POST the universal_variable object to the nToklo servers. nToklo records your store’s user activities, which allows us to provide personalised recommendations as well as informative analytics.

Sometimes you need to send UV object asynchronous, for example some events do not occur on page load. In such cases, you can invoke the sendEvent function. Read more about [Asynchronous Events](async_events.md) if this applies to your website.

## Step 3. Fetch recommendations
Once nToklo has recorded sufficient user activity it can provide good product recommendations. The Recommendations API allows you to fetch recommendations.

Here's how to fetch recommendations in Javascript for the logged in user `nicole12` who is currently previewing `French Sole` shoes:
```javascript
<script type="text/javascript">
  var _ntoklo_key = "NTRjN2M4OWMtMzg1NS00YWNhLWJiODAtMzQzYjYwYWE3YzUx";
  $.ajax({
    type: "GET",
    url: "https://api.ntoklo.com/recommendation?userId=nicole12@yahoo.com&productId=frenchsole_10201&client_key=" + _ntoklo_key,
    dataType: "json"
  }).done(function(data) {
    /* render the recommendation set */
  });
</script>
```
You can also fetch recommendations on the server side. Refer the Recommendations API for examples. Server side authentication requires knowledge of [authentication of requests](auth.md).



