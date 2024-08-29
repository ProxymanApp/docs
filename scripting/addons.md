# Addons

## 1. What's it?

Proxyman provides a list of handy built-in add-ons that help you to do many common tasks, such as MD5, SHA1 Hashing, Base64 Encode/Decode, Beautify XML, JSON, ....&#x20;

### 2. Built-in Addons

You can find sample code for all addons at [Addons Snippet Code](snippet-code.md)

| Name                                                                      | Description                                                                    |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Base64.js](snippet-code.md#use-base64-addon)                             | Base64 Encoding/Decode. Support Native atob/btoa function                      |
| CamelCase.js                                                              | Convert text to Camel Case                                                     |
| CryptoJS.js                                                               | DES, AES, Rabbit encryption/decryption algorithm. A small wrapper of CryptoJS  |
| DateToTimestamp.js                                                        | Convert String Date to Timestamp                                               |
| DateToUTC.js                                                              | Convert String Date to UTC String                                              |
| DecodeURI.js                                                              | Decode percent-encoded String                                                  |
| EncodeURI.js                                                              | Encode to percent-encoded String                                               |
| FormatCSS.js                                                              | Beautify CSS String                                                            |
| FormatJSON.js                                                             | Beautify JSON String                                                           |
| BeautifyJSON.js                                                           | Convert JSON Obj to beauty JSON String                                         |
| UglifyJSON.js                                                             | Convert JSON Obj to ugly JSON String                                           |
| FormatXML.js                                                              | Beautify XML String                                                            |
| HelloWorld.js                                                             | Hello World                                                                    |
| Hex2rgb.js                                                                | Convert #000000 string to RGB string                                           |
| JsonToQuery.js                                                            | Convert JSON Objc to Query String                                              |
| JSONValidator.js                                                          | Validate JSON String                                                           |
| [JWTDecode.js](snippet-code.md#jwt-decode)                                | Decode JWT Token                                                               |
| KebabCase.js                                                              | Conver to Kebab String                                                         |
| [MD5.js](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512)    | Hash MD5                                                                       |
| MinifyCSS.js                                                              | Minify CSS String                                                              |
| MinifyJSON.js                                                             | Minify JSON String                                                             |
| MinifyXML.js                                                              | Minify XML String                                                              |
| QueryToJson.js                                                            | Convert Query String to JSON Object                                            |
| [Pako.js](snippet-code.md#deflate-inflate-and-gzip-ungzip)                | Deflate/Inflate and GZip/UnGZip                                                |
| [SHA1.js](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512)   | Hash SHA1                                                                      |
| [SHA256.js](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512) | Hash SHA256                                                                    |
| [SHA512.js](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512) | Hash SHA512                                                                    |
| SnakeCase.js                                                              | Convert to Snake Case                                                          |
| StartCase.js                                                              | Convert to Start Case                                                          |
| [UUID.js](snippet-code.md#use-uuid-v4-addon)                              | Generate Unique UUID-v4 string                                                 |

## 3. How to use addons?

Each addon will export the function that you can import by using the `require` function

To illustrate, Base64.js addon looks like:

```javascript
// Base64.js
const Base64 = require('@libs/base64.js');
const { atob } = require("@libs/atob.js");
const { btoa } = require("@libs/btoa.js");

// atob / btoa
// They're equivalent with window.atob and window.btoa

exports.atob = atob;
exports.btoa = btoa;

// Basic Base64
exports.base64Decode = (input) => {
    return Base64.decode(input)
};

exports.base64Encode = (input) => {
    return Base64.encode(input);
};
```

Then, you can use it in the script:

```javascript
const { atob, btoa } = require("@addons/Base64.js")

function onRequest(context, url, request) {

    // Encode base64 by using the export function
    var text = btoa("Hello World");
    
    console.log(text)
    // => SGVsbG8gV29ybGQ=
}
```

{% hint style="info" %}
You can find all addons code at **\~/Library/Application\ Support/com.proxyman.NSProxy/addons**
{% endhint %}

## 4. Notes

{% hint style="info" %}
The `require` function is not a built-in function from [JavascriptCore framework](https://developer.apple.com/documentation/javascriptcore), it's a custom function that Proxyman provides to allows the user to import the addons/libs easily.

Thanks to [Ivan Mathy](https://github.com/IvanMathy) for creating Boop app that facilitates Proxyman's built-in add-ons.
{% endhint %}

{% hint style="info" %}
Addons folder will be overridden for every new Proxyman Update. Make sure you don't edit the addon. If need to modify, please copy to the **users** folder
{% endhint %}
