---
description: Prevent caching HTTP Content
---

# No Caching

### 1. What's it?

Prevent the server or client from caching your Request or Response, and you always get the latest change from the server.&#x20;

No Caching tools will affect all HTTP Request and Response, which enabled SSL Proxying.

### 2. What's for?

* If you would like to **see the latest HTTP Response changes** from the Server or Client and ignore all caching layers

### 3. How it works

No Caching tool will manipulate all requests by adding or removing caching HTTP Headers, which are described in the following table.

| HTTP Message | Remove                                       | Add                                                  |
| ------------ | -------------------------------------------- | ---------------------------------------------------- |
| Request      | **If-Modified-Since** and **If-None-Match**  | **Pragma: no-cache** and **Cache-control: no-cache** |
| Response     | **Expires**, **Last-Modified,** and **ETag** | **Expires: 0** and **Cache-Control: no-cache**       |

### 4. How to use

* Enable in **Tool Menu -> No Caching**&#x20;

![](<../.gitbook/assets/Screen Shot 2020-04-25 at 15.45.37.png>)

![No Caching Status on the bottom right of Proxyman app](<../.gitbook/assets/Screen Shot 2020-04-25 at 15.48.05.png>)

{% hint style="info" %}
**⌥⌘N:** Toggl the No Caching Tool.
{% endhint %}
