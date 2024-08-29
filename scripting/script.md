# Scripting

### 1. What's it?

Proxyman offers a scripting feature that the developer could write the JS code to manipulate the Request/Response in a flexible way.&#x20;

### 2. Benefits

* Implement Map Local / Map Remote / Breakpoint by JS Code. **100x Faster**
* Change the **Request Content**, including Domain, Host, Scheme, Port, Path, HTTP Method, HTTP Headers, Query, Body (Encoded-Form, JSON, plain-text)
* Change the **Response Content**, including HTTP Status Code, HTTP Headers, and Body (JSON, Encoded-Form, plain-text, binary...)
* Provide plenty of built-in addons and libraries for common tasks, such as Hashing, Encode/Decode, JSON-Text transformer, Beautify,...
* Able to **write your own JS Addons or Libraries**
* Designed to replace Rewrite GUI Tool from Charles Proxy
* Assign and receive shared States between each script or current session with [ShareState or Environment Variables](environment-variables.md)



<figure><img src="../.gitbook/assets/Screenshot 2024-01-07 at 14.52.47.jpg" alt=""><figcaption><p>Scripting Tool</p></figcaption></figure>

{% content-ref url="snippet-code.md" %}
[snippet-code.md](snippet-code.md)
{% endcontent-ref %}

### 3. How to use it?

You can access the Scripting Tool by:

* Script Menu -> Script List (⌥⌘I)
* Open Menu Context from Right Click on the Flow -> Tools -> Scripting

Please Check out [Snippet Code](snippet-code.md) to see a collection of snippet JS codes for the Scripting Tool.

### 4. Scripting with GraphQL Requests

From Proxyman 2.27.0+, the Scripting Tool can work with GraphQL Request by a specific QueryName. Please check out the following GraphQL Document.

{% content-ref url="../advanced-features/graphql.md" %}
[graphql.md](../advanced-features/graphql.md)
{% endcontent-ref %}

### 5. Examples

The following guide will show you how to write JS code to change the Request domain from Production to Localhost and change the Response Body

1. Make sure you enable SSL for this domain before creating the script)
2. Open the Scripting Tool and create a new Script Entry (⌘N). You can right-click on the Request -> Tools -> Scripting => Proxyman will create a Script too
3. Give the name and define a Matching Rule.&#x20;
4. Ex: **Name**=Test on Localhost endpoint, **URL**=https://proxyman.io
5. Enable Run Script on **Request** and **Response** **checkbox**
6. Start writing JS code for `onRequest` function

**onRequest(context, url, request) {}**

```javascript
// Import UUID addons
const { uuidv4 } = require("@addons/UUID.js");

function onRequest(context, url, request) {
  // print log
  console.log(request);

  // Change Production domain -> Localhost
  request.method = "GET";
  request.scheme = "http";
  request.host = "localhost";
  request.port = 8000;
  
  // Add new header
  request.headers["X-New-Header"] = "Hello From Scripting feature";
  request.headers["UUID"] = uuidv4(); // generate random UUIDv4
  delete request.headers["Key-Need-Delete"];

  // Update or Add a new Query
  request.queries["name"] = "Proxyman";

  // Update Body
  var body = request.body;
  body["name"] = "Proxyman";
  request.body = body;
  
  // Or Map the body with a local file (Proxyman 2.25.0+)
  // request.bodyFilePath = "~/Desktop/mockdata.json";
  
  // Done
  return request;
}
```

### onRequest() Object Format

`context`, `url` and `request` objects are defined by:

```javascript
// context (readonly)
{
    "scriptName": "<String> Your Script Name",
    "matchingRule": "<String> Your Matching Rule",
    "matchingMethod": "<String> Method",
    "isEnableOnRequest": "Bool",
    "isEnableOnResponse": "Bool",
    "filePath": "<String> Script path",
    "flow": { // Availble from 2.16.0+
        "serverPort": "443",
        "serverIpAddress": "104.18.230.83",
        "clientIpAddress": "192.168.0.102",
        "remoteDeviceName": "iPhone XR",
        "remoteDeviceIP": "192.168.0.102",
        "id": "51",
        "clientPath": null,
        "clientPort": "51494",
        "clientName": null
    },
}

// url (readonly)
url: String // => Present the full URL

// request
{
    "method": "<String> HTTP Method. Accept string method. Ex: GET, POST, ...",
    "scheme": "<String> Accept http or https",
    "host": "<String> Host of the request. Ex: api.proxyman.io, localhost, ...",
    "path": "<String>: Path of the URL. Ex: /v1/data",
    "port": "<Int> Accept int port number. Ex: 443, 8080, ..",
    "queries": "<[String: Any]> A JS Object (Dictionary) contains key values of the query",
    "headers": "<[String: Any]> A JS Object (Dictionary) contains key values of the header",
    "body": "Depend on the Content-Type header. It might be a dictionary for JSON and form, Plain Text or Uint8Array",
    "bodyFilePath": "<String><Optional> Set a body with a local file. See example in Snippet Code Page"
    "rawBody": "<Readonly>: A raw body String or Uint8Array",
    "preserveHostHeader": "<Bool> Preserve the Host",
    "isURLEncoding": "<Bool> Determine if Proxyman will perform URLEncoding when constructing the final URL. Default is True"
}

```

{% hint style="info" %}
You can change any value of the request obj except `rawBody`
{% endhint %}

{% hint style="info" %}
If the **body** variable is invalid format due to incorrect Content-Type in the Header. Please consider using the **rawBody** and manually parse the string.
{% endhint %}

The type of `request.body` replies on the Content-Type Header.

| Content-Type Header                                                                 | request.body      |
| ----------------------------------------------------------------------------------- | ----------------- |
| application/json or JSON families                                                   | Javascript Object |
| application/x-www-form-urlencoded                                                   | Javascript Object |
| plain-text or text-based Content-Type, Ex: application/js, text/css, text/html, ... | String            |
| The rest: Binary Data (application/zip, application/octet-stream)                   | Uint8Array        |

Check out common JS code from Snipped Code Page

{% content-ref url="snippet-code.md" %}
[snippet-code.md](snippet-code.md)
{% endcontent-ref %}

7\. Start writing code on `onResponse` function

```javascript
function onResponse(context, url, request, response) {
  console.log(response);

  // Update or Add a new header
  response.headers["Content-Type"] = "application/json";

  // Update status Code
  response.statusCode = 500;

  // Update Body
  var body = response.body;
  body["new-key"] = "Proxyman";
  response.body = body;

  // Or Map the body with a local file (Proxyman 2.25.0+)
  // response.bodyFilePath = "~/Desktop/mockdata.json";
  
  // Done
  return response;
}
```

### onResponse() Objects Format

`context`, `url`, `request`, and `response` objects are defined by:

```javascript
// context (readonly): Same with onRequest

// url (readonly): Same with onRequest

// request (readonly): Same with onRequest

// response
{
    "statusCode": "<Int> Status Code. Ex: 200, 400, 404,...",
    "httpVersion": "<String><Readonly> The HTTP Version",
    "statusPhrase": "<String><Readonly> HTTP Status Phrase. Ex Not Found, OK, ...",
    "headers": "<[String: Any]> A JS Object (Dictionary) contains key values of the header",
    "body": "Depend on the Content-Type header. It might be a dictionary for JSON and form, PlainText or Uint8Array",
    "rawBody": "<Readonly>: A raw body String or Uint8Array",
    "bodyFilePath": "<String><Optional> Set a body with a local file. See example in Snippet Code Page"
}
```

{% hint style="info" %}
You can change `statusCode`, `headers` and `body` from the response Obj
{% endhint %}

{% hint style="info" %}
If the **body** variable is invalid format due to incorrect Content-Type in the Header. Please consider using **rawBody** and manually parse the string.
{% endhint %}

The type of `response.body` replies on the Content-Type Header

| Content-Type Header                                                                 | request.body      |
| ----------------------------------------------------------------------------------- | ----------------- |
| application/json or JSON families                                                   | Javascript Object |
| application/x-www-form-urlencoded                                                   | Javascript Object |
| plain-text or text-based Content-Type, Ex: application/js, text/css, text/html, ... | String            |
| The rest (application/zip, application/octet-stream)                                | Uint8Array        |

{% hint style="info" %}
You must return `request` and `response` object in `onRequest` and `onResponse` function
{% endhint %}

### 6. Built-in Addons and Libraries

Proxyman provides plenty of addons and libraries that help you achieve common tasks: Hashing, Encode/Decode, ...

{% content-ref url="addons.md" %}
[addons.md](addons.md)
{% endcontent-ref %}

{% content-ref url="built-in-js-libraries.md" %}
[built-in-js-libraries.md](built-in-js-libraries.md)
{% endcontent-ref %}

{% content-ref url="snippet-code.md" %}
[snippet-code.md](snippet-code.md)
{% endcontent-ref %}

### 7. Debugging JS Error

On certain occasions, you might encounter Javascript errors due to syntax errors, invalid code, ... You can debug by looking at error messages on the console or using `console.log().`

### 8. Use Scripting as a Mock API

From Proxyman 2.32.0, we can use the Scripting Tool as a Mock API. It means your request would never hit the server, and you have to define a Response Body. This behavior is the same with Map Local.

This feature is useful when the actual Restful API is not available yet. You can define and test it locally.

To enable the Mock API:

1. Open the Scripting Tool -> Select the Script
2. Enable Run as Mock API checkbox.

![Enable Mock API](../.gitbook/assets/Screen\_Shot\_2021-09-17\_at\_14\_59\_30.png)

Then you can define a Response as usual:

```javascript
function onResponse(context, url, request, response) {

  // Init new body
  var body = {};
  body["new-key"] = "Proxyman";
  response.body = body;

  // Or map from a file
  // response.bodyFilePath = "~/Desktop/myfile.json"
  
  // Done
  return response;
}
```

### 9. Notes

* You must return `request` and `response` Object in `onRequest` and `onResponse` function.
* **Proxyman 4.16.0 or later**: Proxyman now converts the Binary Data to **Uint8Array**
* Proxyman 4.15.0 or earlier: Since Javascript doesn't have the Data object type, the Data Body will convert to **Base64 Encoded String** in Javascript. To pass Uint8Array, blob, or ArrayBuffer to the body, make sure you convert to **Base64 Encoded String.**
