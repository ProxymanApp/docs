# async/await Request

## 1. What's it?

From Proxyman macOS v3.5.0 and Windows/Linux v2.11.0 or later, you can use `async / await` to make an HTTP/HTTPS call for retrieving external resources inside your Script.

{% hint style="info" %}
* On macOS: Use \`$http\`
* On Windows/Linux: Use built-in \`axios\`&#x20;
{% endhint %}

#### Sample: POST Request with JSON Body (macOS)

```javascript
async function onResponse(context, url, request, response) {  
  // Define JSON Body and Header
  // Make sure "Content-Type" is "application/json"
  var param = {
    body: {
      "user": {
        "name": "Proxyman"
      }
    },
    headers: {
      "Content-Type": "application/json"
    }
  }

  // POST request with await
  var output = await $http.post("https://httpbin.org/post", param);
  
  // Get Status Code
  console.log(output.statusCode);
  
  // Get body
  console.log(output.body)
  
  // Get header
  console.log(output.headers)
  
  // Done
  return response;
}
```

## 2. How to use on macOS?

#### Method

```javascript
var output = await $http.get("https://httpbin.org/anything");
var output = await $http.post("https://httpbin.org/anything");
var output = await $http.put("https://httpbin.org/anything");
var output = await $http.update("https://httpbin.org/anything");
var output = await $http.delete("https://httpbin.org/anything");
```

#### Output format

```javascript
var output = await $http.get("https://httpbin.org/anything");
console.log(output)

// print
{
    "statusCode": <Int>,
    "headers": <Object>,
    "body": <Object>
}
```

#### Sample Code

* [GET Request with Query](snippet-code.md#get-request-with-query)
* [POST Request with JSON Body](snippet-code.md#post-request-with-json-body)
* [POST Request with application/x-www-form-urlencoded body](snippet-code.md#post-request-with-application-x-www-form-urlencoded-body)
* [PUT / PATCH / DELETE Request](snippet-code.md#put-patch-delete-request)

{% hint style="info" %}
Please checkout the [HTTP Snippet code](snippet-code.md#make-async-await-http-request) for more sample code.
{% endhint %}

## 3. How to use on Windows/Linux?

Proxyman Windows/Linux ships with a built-in [axios](https://github.com/axios/axios) library, it means we can use the axios syntax to make HTTP(s) requests.

For example:

```javascript
async function getUser() {
  try {
    const response = await axios.get('/user?ID=12345');
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```

## 4. Notes

* Make sure you defined the **async** function on `onRequest()` and `onResponse()`:

```javascript
async function onRequest(context, url, request) {
    var output = await $http.get("https://httpbin.org/get");
    return request;
}

async function onResponse(context, url, request, response) {
    var output = await $http.get("https://httpbin.org/get");
    return response;
}
```

* Request Timeout is 10 seconds.
* The inline HTTP Request doesn't go through the Proxyman Proxy, so it isn't affected by other debugging tools.
* Use can use `await $http.get()` on both `onRequest()` and `onResponse()`
* Make sure the Body type is matched with the Content-Type header.

**JSON Body with application/json**

```javascript
var param = {
    body: {
      "name": "Proxyman",
    },
    headers: {
      "Content-Type": "application/json"
    }
  }
```

**Encoded form Body with application/x-www-form-urlencoded**

```javascript
var param = {
    body: {
      "key1": "value1",
      "key2": "value2"
    },
    headers: {
      "Content-Type": "application/x-www-form-urlencoded"
    }
  }
```
