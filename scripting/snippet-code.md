---
description: The collection of useful snippet code for the Scripting tool
---

# Snippet Code

## 1. What's it?

A collection of snippet Javascript code for the Scripting Tool.

{% hint style="info" %}
Could not find the Snippet Code you are looking for?&#x20;

Please open a ticket at [https://github.com/ProxymanApp/Proxyman](https://github.com/ProxymanApp/Proxyman), we will get back to help you ⭐️
{% endhint %}

## 2. Common on Request and Response

* [Update Headers of Request or Response](snippet-code.md#http-header)
* [Update Request Query](snippet-code.md#request-query)
* [Update URLEncoded Form Request Body](snippet-code.md#urlencoded-form-body)
* [Update JSON Request or Response Body](snippet-code.md#json-body)
* [Map a local file to Response's Body like Map Local Tool](snippet-code.md#map-a-local-file-to-responses-body-like-map-local-tool-proxyman-2.25.0+)
* [Change Request Scheme, Host, Port, Path](snippet-code.md#change-request-destination-scheme-host-port-path)
* [HTTP to HTTPS](snippet-code.md#http-to-https)
* [HTTPS to HTTP](snippet-code.md#http-to-https-1)
* [Change Request Method](snippet-code.md#change-response-http-status-code)
* [Change Response Status Code](snippet-code.md#change-response-http-status-code)
* [Logging](snippet-code.md#logging)
* [Use JSON File as a Body of Request or Response](snippet-code.md#use-json-file-as-a-body-of-request-or-response)
* [Use multiple JSON files](snippet-code.md#use-multiple-json-files)
* [Local Map for GraphQL](snippet-code.md#map-local-with-graphql)
* [Use ArrayBuffer in Request/Response Body](snippet-code.md#use-arraybuffer-in-request-response-body)
* [Preserve the Host](snippet-code.md#preserve-the-host)
* [Comment & Highlight with color](snippet-code.md#comment-and-highlight-with-color)
* [Abort (close) the request/response connection (Like Block List Tool)](snippet-code.md#abort-the-request-response-like-block-list-tool)

## 3. Addons&#x20;

* [Base64 Encoding/Decoding or atob/btoa](snippet-code.md#use-base64-addon)
* [Hashing Addon (MD5, SHA1, SHA256, SHA512)](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512)
* [UUIDv4 Generator](snippet-code.md#use-uuid-v4-addon)
* [Deflate/Inflate or GZip/UnGZip](snippet-code.md#deflate-inflate-and-gzip-ungzip)
* [JWT Decode](snippet-code.md#jwt-decode)

## 4. Regex&#x20;

* [Check if a given string contains only numbers](snippet-code.md#regex)
* [Regex to get the Scheme, Host, Port, Path, and Query of the URL](snippet-code.md#regex-to-get-the-scheme-host-port-path-and-query-of-the-url)

## 5. Import / Export Files

* [Import JSON File](snippet-code.md#json)
* [Import Binary Data (Image)](snippet-code.md#binary-file)
* [Import Text-based file (css, html, js....)](snippet-code.md#text-based-file)
* [Import Files without using the "Import Tool"](snippet-code.md#import-file-without-using-the-import-tool)
* [Write / Export to a local file](snippet-code.md#write-export-to-a-local-file)
* [Check file exist](snippet-code.md#check-if-the-first-exist)
* [Read a Local File](snippet-code.md#read-a-file)
* [Use Response as Mock API](snippet-code.md#use-as-mock-api)

## 6. Miscellaneous

* [By-pass CORS](snippet-code.md#by-pass-cors)
* [Inject a Header to the Request or Response](snippet-code.md#inject-header-to-request-response)
* [Response delay with sleep() function](snippet-code.md#response-delay-with-sleep-function)

## 7. Encryption/Decryption

* [AES](snippet-code.md#aes-encryption-decryption)&#x20;
* [DES](snippet-code.md#des-encryption-decryption)

## 8. Map Remote with Scripting

* [Map v1 to v2 Endpoints](snippet-code.md#map-v1-to-v2-endpoints)
* [Map Localhost to Production](snippet-code.md#map-localhost-to-production)
* [Map Production to Localhost](snippet-code.md#map-production-to-localhost)

## 9. Make Async/await HTTP Request (macOS)

* [GET Request with Query](snippet-code.md#get-request-with-query)
* [POST Request with JSON Body](snippet-code.md#post-request-with-json-body)
* [POST Request with application/x-www-form-urlencoded](snippet-code.md#post-request-with-application-x-www-form-urlencoded-body)
* [PUT / PATCH / DELETE Request](snippet-code.md#put-patch-delete-request)

## 9.1. Make Async/await HTTP Request (Windows/Linux)

* [Make a request with the Axios library](snippet-code.md#make-async-await-http-request-windows-linux)

## 10. URL and URLSearchParams

* [URL and URLSearchParams](snippet-code.md#url-and-urlsearchparams)

## 11. Access Environment Variables

* [Manually read system environment variables](snippet-code.md#reload-system-environment-variables)

## HTTP Header

#### Add/Update: Request or Response Header

```javascript
function onRequest(context, url, request) {
    // Add or update Request Header
    request.headers["X-Proxyman-Key"] = "My-Value";
    request.headers.name = "Proxyman";
    return request;
}

function onResponse(context, url, request, response) {
    // Add or update Response Header
    response.headers["X-Proxyman-Key"] = "My-Value";
    response.headers.id = 100;
    return response;
}
```

#### Delete: Request or Response Header

```javascript
function onRequest(context, url, request) {
    delete request.headers["X-Proxyman-Key"];
    return request;
}

function onResponse(context, url, request, response) {
    delete response.headers["X-Proxyman-Key"];
    return response;
}

```

## Request Query

#### Add/Update

```javascript
function onRequest(context, url, request) {
    request.queries["name"] = "Proxyman";
    request.queries["platform"] = "macOS";
    // => http://proxyman.io?name=Proxyman&platform=macOS
    return request;
}
```

#### Delete

```javascript
function onRequest(context, url, request) {
    delete request.queries["name"];
    delete request.queries["platform"];
    return request;
}

```

## URLEncoded Form Body

#### Add/Update

```javascript
function onRequest(context, url, request) {
    // Make sure the Response Header is application/x-www-form-urlencoded
    // Content-Type: application/x-www-form-urlencoded   
    var formBody = request.body;

    formBody["name"] = "Proxyman";
    formBody["flatform"] = "macOS";

    request.body = formBody; // => name=Proxyman&platform=macOS
    return request;
}

```

#### Delete&#x20;

```javascript
function onRequest(context, url, request) {
    // Content-Type: application/x-www-form-urlencoded
    var formBody = request.body;

    delete formBody["name"];
    delete formBody["flatform"];

    request.body = formBody;
    return request;
}

```

## Change Request Destination (scheme, host, port, path)

```javascript
function onRequest(context, url, request) {
    request.scheme = "http";
    request.host = "proxyman.dev";
    request.port = 9090;
    request.path = "v1/data/user";
    return request;
}
```

## HTTP to HTTPS

```javascript
function onRequest(context, url, request) {
    request.scheme = "http";
    request.port = 80; // Don't forget to override the port
    return request;
}
```

## HTTPS to HTTP

```javascript
function onRequest(context, url, request) {
    request.scheme = "https";
    request.port = 443; // Don't forget to override the port
    return request;
}
```

## Change HTTP Request Method

```javascript
function onRequest(context, url, request) {
    request.method = "POST";
    return request;
}
```

## Change Response HTTP Status Code

```javascript
function onResponse(context, url, request, response) {
    response.statusCode = 404;
    return response;
}
```

## JSON Body

#### On Request

```javascript
function onRequest(context, url, request) {
    // Set JSON content
    request.headers["Content-Type"] = "application/json";
    
    // Get Request body
    var jsonBody = request.body;
    
    // Modify data
    jsonBody["name"] = "Proxyman";
    jsonBody["flatform"] = "macOS";
    jsonBody["info"] = { 
                        "website": "proxyman.io",
                        "region": "Earth"
                       };
    // Set it again        
    request.body = jsonBody;
    return request;
}
```

#### On Response

```javascript
function onResponse(context, url, request, response)  {
    // Set JSON content
    response.headers["Content-Type"] = "application/json";
  
    // Get Request body
    var jsonBody = response.body;
    
    // Modify data
    jsonBody["name"] = "Proxyman";
    jsonBody["flatform"] = "macOS";
    jsonBody["info"] = { 
                        "website": "proxyman.io",
                        "region": "Earth"
                       };
    // Set it again        
    response.body = jsonBody;
    return response;
}

```

#### Map a local file to Response's Body like Map Local Tool (Proxyman 2.25.0+)

It's a convenient way to directly set a local file to a Body by using `bodyFilePath` property

```javascript
// For request
request.bodyFilePath = "~/Desktop/image.png";

// For response
response.bodyFilePath = "~/Desktop/image.png";
```

```javascript
function onResponse(context, url, request, response) {
 
  response.headers["Content-Type"] = "image/png";
  response.bodyFilePath = "~/Desktop/image.png";
 
  // Done
  return response;
}
```

```javascript
function onResponse(context, url, request, response) {
 
  response.headers["Content-Type"] = "application/json";
  response.bodyFilePath = "~/Desktop/my_response.json";
 
  // Done
  return response;
}
```

#### Use JSON File as a Body of Request or Response

It's possible to use your JSON file and set it as a Request/Response's body

Please follow this [tutorial](snippet-code.md#json).

#### Use multiple JSON files

You can use set a different body for each matching endpoint by using the IF statement.

1. Follow this [tutorial](snippet-code.md#json) to understand how to import a JSON file to the script
2. Set Script Rule with wildcard or Regex pattern that can match many endpoints. E.g https://my-domain.com/v\*
3. Use \`includes()\` to check whether or not the endpoint is matched

```javascript
const file_1 = require("@users/myfile_1.json");
const file_2 = require("@users/myfile_2.json");
const file_3 = require("@users/myfile_3.json");

function onResponse(context, url, request, response) {
  
  // Set JSON content
  response.headers["Content-Type"] = "application/json";
  
  // Check
  if (url.includes("v1/data")) {
    response.body = file_1
  } else if (url.includes("v2/login")) {
      response.body = file_2
  } else if (url.includes("v3/user")) {
      response.body = file_3
  }

  // Done
  return response;
}
```

#### Map Local with GraphQL

Read more at [https://github.com/ProxymanApp/Proxyman/issues/412#issuecomment-697101594](https://github.com/ProxymanApp/Proxyman/issues/412#issuecomment-697101594)

```javascript
// Import your JSON file here 
const file = require("@users/B02D96D5.default_message_32E64A5B.json");

function onRequest(context, url, request) {

  // 1. Extract the queryName from the request
  var queryName = request.body.query.match(/\S+/gi)[1].split('(').shift();

  // 2. Save to sharedState
  sharedState.queryName = queryName

  // Done
  return request;
}

function onResponse(context, url, request, response) {

  // 3. Check if it's the request we need to map
  if (sharedState.queryName == "user") {
    
    // 4. Import the local file by Action Button -> Import
    // Get the local JSON file and set it as a body (like Map Local)
    response.headers["Content-Type"] = "application/json";
    response.body = file;
  }

  // Done
  return response;
}
```

#### Use ArrayBuffer in Request/Response Body

Since Javascript doesn't have the Data object type, the Data Body will convert to **Base64 Encoded String** in Javascript. To pass **Uint8Array**, **blob**, or **ArrayBuffer** to the body, make sure you convert to **Base64 Encoded String** and set the ContentType to `application/octet-stream`

Proxyman will convert Base64 Encoding to ArrayBuffer, so the client will receive the data properly.&#x20;

```javascript
// Import
const { btoa } = require('@addons/Base64.js');

function onResponse(context, url, request, response) {
  // Construct the ArrayBuffer
  const buffer = new ArrayBuffer(256)
  const view = new Uint8Array(buffer)
  for (let i = 0; i < view.length; i++) {
    view[i] = i
  }
  
  // Convert ArrayBuffer to Base64String
  var newBody = btoa(String.fromCharCode.apply(null, new Uint8Array(buffer)));
  
  // Set new body
  response.body = newBody;
  response.statusCode = 200
  response.headers['Content-Type'] = 'application/octet-stream'

  // Done
  return response;
}
```

#### Preserve the Host

```javascript
function onRequest(context, url, request) {
    request.preserveHostHeader = true
    return request
}
```

#### Comment & Highlight with color

Use `comment` or `color` to highlight on the main table view.

```javascript
function onRequest(context, url, request) {
    request.comment = "It's a Request"
    request.color = "red" // red, blue, yellow, purple, gray, green
    return request
}

function onResponse(context, url, request, response) {
    response.comment = "It's a Response"
    response.color = "yellow" // red, blue, yellow, purple, gray, green
    return response
}
```

![Use Scripting for Color and Comment](../.gitbook/assets/Screen\_Shot\_2021-08-13\_at\_09\_27\_36.png)

## Import Files with require()

#### JSON

1. Prepare a JSON file and save it to your Desktop

```javascript
// myfile.json
{
  "name": "Proxyman",
  "platform": "macOS",
  "info": {
    "website": "proxyman.io",
    "region": "Earth"
  }
}
```

2\. More -> Import JSON or Other Files. Then selecting your file&#x20;

![](<../.gitbook/assets/Screen Shot 2021-04-22 at 10.59.46.png>)

3\. Proxyman will add the import code to the top of the script

```javascript
// ~/Library/Application Support/com.proxyman.NSProxy/users/myfile.json
const file = require("@users/myfile.json");

function onResponse(context, url, request, response) {
  // 1. Set header to JSON if need
  response.headers["Content-Type"] = "application/json";

  // 2. Set Body as a imported file
  response.body = file;
  
  return response;
}
```

{% hint style="info" %}
The selected file is copied to **\~/Library/Application\ Support/com.proxyman.NSProxy/users** folder.
{% endhint %}

{% hint style="info" %}
To support other format files, such as image, text, pdf. Make sure you have correct **Header Content-Type**
{% endhint %}

#### Binary File

1. Follow the same above instruction (Select your Binary File)
2. Set it as a body

```javascript
// ~/Library/Application Support/com.proxyman.NSProxy/users/myscreenshot.png
const file = require("@users/myscreenshot.png");

function onResponse(context, url, request, response) {
  // Set header
  response.headers["Content-Type"] = "image/png";

  // Set Body
  response.body = file;
  
  return response;
}
```

#### Text-Based File

1. Follow the same above instruction (Select your Binary File)
2. Set it as a body

```javascript
// ~/Library/Application Support/com.proxyman.NSProxy/users/main.css
const file = require("@users/main.css");

function onResponse(context, url, request, response) {
  // Set header
  response.headers["Content-Type"] = "text/css";

  // Set Body
  response.body = file;
  
  return response;
}
```

#### Import File without using the "Import Tool"

From Proxyman 2.24.0+, you can import any files without using the "Import File".

```javascript
// Import your file from your Desktop folder
const file = require("~/Desktop/myfile.json");

function onResponse(context, url, request, response) {

  // 1. Set header to JSON if need
  response.headers["Content-Type"] = "application/json";

  // 2. Set Body as a imported file
  response.body = file;
  
  return response;
}
```

* If the file has ".js" as an extension => Proxyman will execute it as a JS Script
* Otherwise, Proxyman will import it as normal

{% hint style="info" %}
Only files that are imported by using the "Import Tool", are included when exporting the script to your colleague.
{% endhint %}

#### Use as Mock API

You can use Scripting as a Mock API by following this [guideline](https://docs.proxyman.io/scripting/script#8-use-scripting-as-a-mock-api).

## Using Addons

[Full list of built-in addons](addons.md)

#### Use Base64 Addon

```javascript
// Encode Base64
const { btoa } = require("@addons/Base64.js")

// Usage:
var text = "HelloWorld";
var encodedText = btoa(text);
```

```javascript
// Decode Base64
const { atob } = require("@addons/Base64.js")

// Usage:
var text = atob("aGVsbG8=");
```

#### Use Hashing Addon (MD5, SHA1, SHA256, SHA512)

```javascript
// Hash MD5
const { md5 } = require("@addons/MD5.js")

// Usage:
var hashedText = md5("Hello World");
```

```javascript
// Hash SHA1
const { sha1 } = require("@addons/SHA1.js")

// Usage:
var hashedText = sha1("Hello World");
```

#### Use UUID-v4 Addon

```javascript
// Hash MD5
const { uuidv4 } = require("@addons/UUID.js")

// Usage:
var uuid = uuidv4();
```

## Deflate/Inflate and GZip/UnGZip

#### Deflate/inflate

```javascript
const { inflate, deflate } = require("@addons/Pako.js")

// Compress
var input = "Hello World from Pako!!!"
var result = deflate(input);
console.log(result); // eJzzSM3JyVcIzy/KSVFIK8rPVQhIzM5XVFQEAGsMB/8=

// Decompress
var text = 'eJzzSM3JyVcIzy/KSVFIK8rPVQhIzM5XVFQEAGsMB/8=';
var rawText = inflate(text);
console.log(rawText); // Hello World from Pako!!!
```

#### GZip/UnGZip

```javascript
const { ungzip, gzip } = require("@addons/Pako.js")

// Compress
var text =  'HelloWorld';
var result = gzip(text);
console.log(result); // H4sIAAAAAAAAA/NIzcnJD88vykkBAHkMd3cKAAAA

// Decompress
var text =  'H4sIAAAAAAAAA/NIzcnJD88vykkBAHkMd3cKAAAA';
var rawText = ungzip(text);
console.log(rawText); // HelloWorld
```

#### JWT Decode

```javascript
const { jwtDecode } = require('@addons/JWTDecode.js');

var text = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c';
var jSONObject = jwtDecode(text)
```

## Logging

```javascript
// Print the obj
const myObj = {};
console.log(myObj);

// Print type of the obj
console.log(typeof(myObj));
```

## Regex

#### Only number

```javascript
//Init Regex
var reg = /^-?\d*\.?\d*$/;

if (reg.test("123123123")) {
    console.log("Matched");
}
```

#### Regex to get the Scheme, Host, Port, Path, and Query of the URL

```javascript
function onRequest(context, url, request) {
  console.log(url);

  // Get each part
  const regex = /^(https?):\/\/([^:\/\n]+)(?::(\d+))?([^#\n?]+)(?:\?([^#\n]+))?/;
  const [, scheme, host, port, path, query] = url.match(regex);

  // Assign again
  request.scheme = scheme;
  request.host = host;
  if (port !== undefined) {
    request.port = parseInt(port);
  }
  request.path = path;

  // Log
  console.log("----------");
  console.log(scheme);
  console.log(host);
  console.log(port);
  console.log(path);

  // Done
  return request;
}
```

## Miscellaneous

#### By-pass CORS&#x20;

```javascript
function onResponse(context, url, request, response) {  

  // Allow all
  response.headers["Access-Control-Allow-Origin"] = "*";
  response.headers["Access-Control-Allow-Headers"] = "*"；
  response.headers["Access-Control-Allow-Methods"] = "*";

  // Done
  return response;
}
```

#### Inject Header to Request / Response&#x20;

```javascript
function onRequest(context, url, request) {
  // add header
  request.headers["My-Injected-Header"] = "Proxyman";
  return request
}

function onResponse(context, url, request, response) {    
  // add header
  response.headers["My-Injected-Header"] = "Proxyman";
  return response;
}

```

#### Response delay with sleep() function

It's useful for simulating the "Slow Network" on a particular Request or Response. You can check out the [Network Conditions tool](../advanced-features/network-throttling.md#1.-whats-it) for GUI.

```javascript
function onResponse(context, url, request, response) {
  console.log("Start sleep");
  
  // Sleep 5 seconds
  sleep(5000);
  
  // Done
  return response;
}
```

#### AES Encryption/Decryption

```javascript
const { encryptAES, decryptAES } = require("@addons/CryptoJS.js")

function onRequest(context, url, request) {
  
  // Encrypt
  var message = 'my message from Proxyman';
  var password = 'secret key 123';
  var ciphertext = encryptAES(message, password);
  
  // Decrypt
  var originalText = decryptAES(ciphertext, password);

  // Done
  return request;
}
```

#### DES Encryption/Decryption

```javascript
const { encryptDES, decryptDES } = require("@addons/CryptoJS.js")

function onRequest(context, url, request) {
  
  // Encrypt
  var message = 'my message from Proxyman';
  var password = 'secret key 123';
  var ciphertext = encryptDES(message, password);
  
  // Decrypt
  var originalText = decryptDES(ciphertext, password);

  // Done
  return request;
}
```

#### Write / Export to a local file

* Override Mode

```javascript
function onResponse(context, url, request, response) {

  // Write to single file
  writeToFile(response.body, "~/Desktop/body.json");
  
  // Write the Body to file with flow ID
  writeToFile(response.body, "~/Desktop/sample-" + context.flow.id);
  
  // Done
  return response;
}
```

* Append Mode (Only for Proxyman 3.6.2+)

```javascript
async function onResponse(context, url, request, response) {

  // Append to the existed file
  // Or create a new file if it doesn't exist
  var opt = {appendFile: true}
  writeToFile(response.body, "~/Desktop/body.json", opt);

  // Done
  return response;
}
```

#### Check if the first exist&#x20;

* Available: Proxyman macOS 5.4.0+

```javascript
async function onRequest(context, url, request) {

  const filePath = "~/Desktop/myfile.json"
  
  // check if the file exists
  if (isFileExists(filePath)) {
    console.log("File exists");
  } else {
    console.log("File NOT exists");  
  }
  
  // Done
  return request;
}
```

#### Read a file

* If it's text-based -> Return a **String**
* Otherwise -> Return **Uint8Array**
* Available: Proxyman macOS 5.4.0+

```javascript
async function onRequest(context, url, request) {  // console.log(request);

  const textFilePath = "~/Desktop/myfile.json";
  
  // check exist
  if (isFileExists(filePath)) {
  
    // read from file
    const text = readFromFile(textFilePath);
    
    // pares string to JSON Object
    const obj = JSON.parse(text);
  }
  
  // Read binary file
  const binaryFilePath = "~/Desktop/screenshot.png";
  const binaryFile = readFromFile(binaryFilePath); // Uint8Array
  
  // Done
  return request;
}
```

## Map Remotes

#### Map v1 to v2 endpoints

```javascript
function onRequest(context, url, request) {
  
  // Replace v1 to v2 in URL Path
  var newPath = request.path.replace("v1", "v2");
  request.path = newPath

  // Done
  return request;
}
```

#### Map localhost to production

```javascript
function onRequest(context, url, request) {
  
  // Use production URL
  request.scheme = "https";
  request.host = "proxyman.io";
  request.port = 443;

  // Done
  return request;
}
```

#### Map production to localhost

```javascript
function onRequest(context, url, request) {
  
  // Use production URL
  request.scheme = "http";
  request.host = "localhost";
  request.port = 3000;

  // Done
  return request;
}
```

## Make async/await HTTP Request (macOS)

{% hint style="info" %}
This feature \`$http\` is available on the macOS version. To use on Windows, please check the next part.
{% endhint %}

#### GET Request with Query

```javascript
async function onResponse(context, url, request, response) {  
  // GET Request with Query
  var url = "https://httpbin.proxyman.app/get?id=proxyman&country=united%20states";
  var output = await $http.get(url);
  
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

#### POST Request with JSON Body

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
  var output = await $http.post("https://httpbin.proxyman.app/post", param);
  
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

#### POST Request with application/x-www-form-urlencoded body

```javascript
async function onResponse(context, url, request, response) {  
  // Define form Body and Header
  // Make sure "Content-Type" is "application/x-www-form-urlencoded"
  var param = {
    body: {
      "key1": "value1",
      "key2": "value2"
    },
    headers: {
      "Content-Type": "application/x-www-form-urlencoded"
    }
  }

  // POST request with await
  var output = await $http.post("https://httpbin.proxyman.app/post", param);
  
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

#### PUT / PATCH / DELETE Request

```javascript
async function onRequest(context, url, request) {  

  var param = {
    body: {
      "user": {
        "name": "Proxyman"
      }
    },
    headers: {
      "Content-Type": "application/json"
  }


  var output = await $http.post("https://httpbin.proxyman.app/post", param);
  var output = await $http.put("https://httpbin.proxyman.app/put", param);
  var output = await $http.delete("https://httpbin.proxyman.app/delete", param);
  
  // Done
  return request;
}
```

## Make async/await HTTP Request (Windows/Linux)

Windows/Linux ships with a built-in [Axios](https://github.com/axios/axios) library. You can easily make HTTP(s) requests with \`Axios\` syntax.

```javascript
async function getUser() {
  try {
    const response = await axios.get('https://httpbin.proxyman.app/user?ID=12345');
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```

### Abort the request/response like Block List Tool

* Only available for Proxyman 3.11.0 and later

#### Abort the request

```javascript
function onRequest(context, url, request) {
  // drop the connection
  abort();
}
```

```javascript
function onRequest(context, url, request) {

  // Use the if to abort on certain conditions
  if (true) {
    abort();
    return; // Must return a void to stop the func
  }

  // Done
  return request;
}
```

#### Abort the response

```javascript
function onResponse(context, url, request, response) {    
  // drop the connection
  abort();
}
```

### URL and URLSearchParams

From Proxyman 4.13.0 or later, [URL](https://developer.mozilla.org/en-US/docs/Web/API/URL) and [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) are natively supported.

```javascript
function onRequest(context, url, request) {

  // URL
  const urlObj = new URL("https://proxyman.io/api/v1/user?id=123");
  console.log(urlObj.hostname);
  console.log(urlObj.search);
  console.log(urlObj.searchParams);

  // URLSearchParmas
  const params1 = new URLSearchParams("foo=1&bar=2");
  
  // Done
  return request;
}
```

### Reload System Environment Variables

Proxyman macOS 4.15.0 or later.

Make sure we enable the permission first, in the More Button -> Environment Variables -> Allow all scripts to read env.

```javascript
async function onRequest(context, url, request) {
  // manually reload to get the latest changes
  _reloadEnv();
  
  // get env
  console.log($PROXYMAN_ID)
  
  // Done
  return request;
}
```
