![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)

## Server-side authentication

Server-side requests to the nToklo API must be signed using SHA1-HMAC and your API secret. For example, to fetch recommendations using a signed request to authenticate:

### Step 1. Produce the request signature

- Construct a basestring from the request. Notice the format of the basestring, `<HTTP_METHOD>&<REQUEST_URI>`:
`GET&https://api.ntoklo.com/recommendation?userId=112&productId=10201`

- Construct a key to be used for SHA1 encryption; it should have the format `client_key&client_secret`:
`YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5&MmExMzY0ZGUtMjc0ZS00NWMyLWExNDMtM2U3OTc4ODljODI2`

- Base64 encode the resulting HMAC_SHA1 hash. This is your request signature:
`1d0570f3c1995bfa3974a35731b17ecb51f6b6fb`

Here’s a code example of signing a request using the Python Interpreter:

```
>>> import hmac
>>> from hashlib import sha1
>>> client_key = "YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5"
>>> client_secret = "MmExMzY0ZGUtMjc0ZS00NWMyLWExNDMtM2U3OTc4ODljODI2"
>>> uri = "https://api.ntoklo.com/recommendation?userId=112&productId=10201"
>>> http_method = "GET"
>>> basestring = "%s&%s" % (http_method, uri)
>>> sha1_key = "%s&%s" % (client_key, client_secret)
>>> signature = hmac.new(sha1_key, basestring, sha1).hexdigest()
>>> print signature
1d0570f3c1995bfa3974a35731b17ecb51f6b6fb
>>>
```

### Step 2. Authorisation header
In order for your request to be authenticated you must provide the Authorization header, which should contain you API key and request signature in the format client_key:signature. The authorisation realm should be NTOKLO.

```
GET /recommendation?userId=112&productId=10201
Host: api.ntoklo.com
Authorization: NTOKLO YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5:2fa162cb5309764f5efe30fc007684bf29615a9b
```

## Client-side authentication
nToklo also supports client-side requests via Javascript.

In order to authenticate your client-side request you must specify your **API key** via request parameter. Here’s an example of making a client-side request using jQuery:

```
$.ajax({
  type: "GET",
  dataType: "json",
  url: "https://api.ntoklo.com/recommendation"
    + "?client_key=YzZkYmI2ZGUtYTNiYS00NWQ5LThjOWMtODZiZDBhNzljZjM5"
    + "&userId=112&productId=10201"
}).done(function(data) {
  console.log("Response: " + JSON.stringify(data));
});
```