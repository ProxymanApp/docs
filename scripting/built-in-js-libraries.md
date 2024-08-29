# Built-in JS Libraries

### 1. What's it?

Proxyman provides certain useful bundled JS Libraries that help you achieve some tasks easily

{% hint style="info" %}
Library Location: **\~/Library/Application\ Support/com.proxyman.NSProxy/addons/libs**
{% endhint %}

### 2. Built-in Libraries

| Name             | Description                                                                                                            | Source                                                                               |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| base64.js        | Contains basic Base64 Encode/Decode                                                                                    | -                                                                                    |
| atob.js          | window.atob()                                                                                                          | [https://github.com/jsdom/abab](https://github.com/jsdom/abab)                       |
| btoa.js          | window.btoa()                                                                                                          | [https://github.com/jsdom/abab](https://github.com/jsdom/abab)                       |
| hashes.js        | Contains various hashing function: MD5, RIPEMP-160, SHA1, SHA256, SHA512, HMAC                                         | [https://github.com/h2non/jshashes](https://github.com/h2non/jshashes)               |
| lodash.js        | Contains various text transformed functions                                                                            | [https://lodash.com](https://lodash.com)                                             |
| vkBeautify.js    | pretty-print or minify text in XML, JSON, CSS and SQL formats.                                                         | [https://github.com/kayhadrin/vkBeautify/](https://github.com/kayhadrin/vkBeautify/) |
| crypto-js.min.js | JavaScript implementations of standard and secure cryptographic algorithms, e.g. DES, AES, Rabbit, ... (Version 3.3.0) | [https://cryptojs.gitbook.io/docs/](https://cryptojs.gitbook.io/docs/)               |

### 3. How to import my own JS Library?

1. You can provide your own JS Library, but make sure you bundle all dependencies by using [Browserify](http://browserify.org) or [WebPack](https://webpack.js.org) to a single JS file.
2. Make sure you export the func properly.
3. Put the file at **\~/Library/Application\ Support/com.proxyman.NSProxy/addons/libs/your-lib.js**
4. Importing the file by using&#x20;

```javascript
require('@libs/your-lib.js');
```

For instance,

```javascript
const Hashes = require('@libs/hashes.js');
const { cssmin } = require('@libs/vkBeautify.js');
const Lodash = require('@libs/lodash.js');
const { atob } = require('@lib@atob.js')
```

{% hint style="info" %}
You might check built-in libraries for reference at **\~/Library/Application\ Support/com.proxyman.NSProxy/addons/libs/**
{% endhint %}

### 4. Notes

{% hint style="info" %}
Thanks to [Ivan Mathy](https://github.com/IvanMathy) for creating Boop app that facilitates Proxyman's built-in add-ons.
{% endhint %}

