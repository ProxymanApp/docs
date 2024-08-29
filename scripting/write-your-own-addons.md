# Write your own Addons

## 1. What's it?

You can write your own Addon to achieve what Proxyman hasn't provided yet. You can do:

* Write your own Javascript Addon.
* Use [Built-in Libraries](built-in-js-libraries.md).
* Write your library and share it with your colleauges.

## 2. How to write an addon?&#x20;

1. Open User Addon folder at `~/Library/Application\ Support/com.proxyman.NSProxy/users` or you can open by opening the More Button -> Documentations -> Open Custom Addons Folder...

![](<../.gitbook/assets/Screen Shot 2021-08-13 at 20.37.39.png>)

2\. Duplicate `HelloWorld.js` file and rename it to **MyAwesomeAddon.js**

3\. Open the file and you can see the template.

4\. Change the metadata and write your JS Code

```javascript
/**
    {
        "name":"My Awesome Addon",
        "description":"The first User Addons",
        "author":"Proxyman",
        "tags":"helloworld"
    }
**/

const { md5 } = require("@addons/MD5.js");

const sayHello = () => {
  var content = "Hello World. My first custom Addon.";
  var hash = md5(content);
  return content + ". MD5 = " + hash;
};

// Make sure you export the function at the end of method
exports.sayHello = sayHello;

```

* You can import built-in addons by using **require(@"addons/\<name.js>")**

```javascript
const { md5 } = require("@addons/MD5.js");
```

{% hint style="info" %}
Check out the [built-in addons ](addons.md#2-built-in-addons)that Proxyman provides
{% endhint %}

* You can import a built-in library by using **require(@"lib/\<name.js>")**

{% hint style="info" %}
Check out the [built-in library](built-in-js-libraries.md) that Proxyman provides
{% endhint %}

5\. Save the file

6\. Open your Script in Proxyman app and import the script&#x20;

```javascript
// Import your addon
// Make sure you imports the function that you exports in the addons
const { sayHello } = require("@users/MyAwesomeAddon.js");

// Usage
sayHello();
```

{% hint style="info" %}
**require("@users/MyAwesomeAddon.js")** is your addon directory

@users is the Custom Addons Folder.
{% endhint %}

## 3. Note

{% hint style="info" %}
Your own scripts are stored at **\~/Library/Application\ Support/com.proxyman.NSProxy/users**

This folder is safe. It's never overridden or removed by Proxyman.
{% endhint %}
