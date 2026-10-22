---
description: >-
  Browse the built-in Proxyman Scripting addons for Base64, MD5/SHA hashing,
  UUID, JWT decode, GZip and more, and import them with require().
---

# Addons

## 1. What's it?

Proxyman provides handy built-in addons for common tasks, such as MD5 and SHA1 hashing, Base64 encode/decode, and beautifying XML and JSON.

{% hint style="success" %}
From Proxyman macOS 6.10.0 or later, you can use the native \`npm install\` to install your 3rd-party libraries. See [use-npm-install.md](use-npm-install.md "mention").
{% endhint %}

## 2. Built-in Addons

You can find sample code for all addons at [Addons Snippet Code](snippet-code.md)

| Name                                                                      | Description                                                                   |
| ------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| [Base64.js](snippet-code.md#use-base64-addon)                             | Base64 encode/decode. Supports native atob/btoa functions                     |
| CamelCase.js                                                              | Convert text to Camel Case                                                    |
| CryptoJS.js                                                               | DES, AES, Rabbit encryption/decryption algorithm. A small wrapper of CryptoJS |
| DateToTimestamp.js                                                        | Convert String Date to Timestamp                                              |
| DateToUTC.js                                                              | Convert String Date to UTC String                                             |
| DecodeURI.js                                                              | Decode percent-encoded String                                                 |
| EncodeURI.js                                                              | Encode to percent-encoded String                                              |
| FormatCSS.js                                                              | Beautify CSS String                                                           |
| FormatJSON.js                                                             | Beautify JSON String                                                          |
| BeautifyJSON.js                                                           | Convert JSON Object to a pretty JSON String                                   |
| UglifyJSON.js                                                             | Convert JSON Object to a compact JSON String                                  |
| FormatXML.js                                                              | Beautify XML String                                                           |
| HelloWorld.js                                                             | Hello World                                                                   |
| Hex2rgb.js                                                                | Convert #000000 string to RGB string                                          |
| JsonToQuery.js                                                            | Convert JSON Object to Query String                                           |
| JSONValidator.js                                                          | Validate JSON String                                                          |
| [JWTDecode.js](snippet-code.md#jwt-decode)                                | Decode JWT Token                                                              |
| KebabCase.js                                                              | Convert to Kebab Case                                                         |
| [MD5.js](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512)    | Hash MD5                                                                      |
| MinifyCSS.js                                                              | Minify CSS String                                                             |
| MinifyJSON.js                                                             | Minify JSON String                                                            |
| MinifyXML.js                                                              | Minify XML String                                                             |
| QueryToJson.js                                                            | Convert Query String to JSON Object                                           |
| [Pako.js](snippet-code.md#deflate-inflate-and-gzip-ungzip)                | Deflate/Inflate and GZip/UnGZip                                               |
| [SHA1.js](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512)   | Hash SHA1                                                                     |
| [SHA256.js](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512) | Hash SHA256                                                                   |
| [SHA512.js](snippet-code.md#use-hashing-addon-md-5-sha-1-sha-256-sha-512) | Hash SHA512                                                                   |
| SnakeCase.js                                                              | Convert to Snake Case                                                         |
| StartCase.js                                                              | Convert to Start Case                                                         |
| [UUID.js](snippet-code.md#use-uuid-v4-addon)                              | Generate Unique UUID-v4 string                                                |

## 3. How to use addons?

Each addon exports functions that you can import with the `require` function.

For example, the Base64.js addon looks like this:

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
The `require` function is not a built-in function from [JavascriptCore framework](https://developer.apple.com/documentation/javascriptcore), it's a custom function that Proxyman provides so you can import addons and libraries easily.

Thanks to [Ivan Mathy](https://github.com/IvanMathy) for creating Boop app that facilitates Proxyman's built-in add-ons.
{% endhint %}

{% hint style="info" %}
The addons folder is overwritten by every Proxyman update, so don't edit the addons there. To change an addon, copy it to the **users** folder first. See [Write your own Addons](write-your-own-addons.md).
{% endhint %}
