# Block List

### 1. What's it?

Block List Tool is useful when you would like to **block / Hide** certain domains during debugging session.

For instance, you can use Block List in the following situations:

* Block all ads requests from particular domains
* Block all analytic requests that flood the working space
* Block all annoying ping requests from your app to reduce the number of requests that appear on Proxyman
* Hide analytic traffic from your website without blocking them.

All blocked domains in the Block List will **drop the connection.**



![Block / Hide List](<../.gitbook/assets/Screen Shot 2022-01-10 at 14.40.39.png>)

### 2. Block Actions

Block List supports variables block actions that can suit your needs:

| Block Action         | Description                                                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Block & Hide Request | Matched requests are blocked and don't display on the app.                                                                     |
| Block & Display      | Matched requests are blocked, but display the blocked requests on the app.                                                     |
| Hide, but not Block  | Just hiding the matched requests without blocking them. It's useful if you'd hide your annoying requests but don't block them. |

![Create a Block / Hide Rule](<../.gitbook/assets/Screen Shot 2022-01-10 at 14.43.38.png>)

### 3. How to use it?

* **Tools** Menu -> **Block List**
* Right-click on the requests or domains -> **Tools** -> **Block List...**

{% hint style="info" %}
**⌥⌘\[** to quick open Block List Window
{% endhint %}
