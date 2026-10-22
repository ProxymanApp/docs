---
description: "Add Proxyman Custom Previewer Tabs to show a request or response body as JSON, Protobuf, HTML or MessagePack, or to add the Connection Log tab."
---

# Custom Previewer Tab

## 1. What's it?

Custom Previewer Tabs let you add extra tabs to the Request and Response panels. Each tab always renders the content in one format.

This handy tool helps in the following cases:

* Format the BODY as **JSON**, but the Content-Type isn't `application/json`
* Format the body as **Protobuf**, but the Content-Type isn't `application/x-protobuf`
* Render an HTML page in a Web View
* **Beautify** the minified files (HTML, CSS, JS)
* Multipart/form-data
* Try to format the body as the selected type regardless of the `Content-Type`
* Convert MessagePack (msgpack) to JSON
* [Code Generator](../advanced-features/code-generator.md) to Swift, Node, Javascript, cURL, ...
* GraphQL Query Prettier
* [Connection Log](connection-log.md) to inspect DNS, TCP, TLS, and HTTP details

<div data-full-width="false"><figure><img src="../.gitbook/assets/Screenshot 2024-06-27 at 15.01.33.png" alt="Proxyman Custom Previewer Tab window with format checkboxes for the Request and Response panels" width="563"><figcaption><p>Select Custom Tabs for Request / Response Panel</p></figcaption></figure></div>

{% hint style="info" %}
The selected custom tabs are added to the right side of the Request or Response view&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/CleanShot 2024-06-27 at 15.04.11@2x.jpg" alt="Proxyman main window with custom Summary and mytab tabs in the Request panel and Treeview and HTML tabs in the Response panel"><figcaption><p>Display Custom Tabs</p></figcaption></figure>

## 2. How to use it?

To open the Custom Previewer Tab window:

1. Click the "+" button on the Request/Response tab bar, or go to **Tools** → **Custom Previewer Tab…**
2. Check or uncheck a checkbox to show or hide your custom tab
3. The new tab appears on the Request or Response panel ✅

### 2.1 Server-Sent Events and OpenAI Tabs

From Proxyman 5.22.0 or later, Proxyman supports:

* **SSE** tab for Server-Sent Events from OpenAI endpoints: Auto-prettify the inline JSON of each data event
* **OpenAI** tab: Auto-merge the streamed content and show the final result, similar to the output in your chat view.

<figure><img src="../.gitbook/assets/1.jpg" alt="Proxyman SSE tab showing a prettified OpenAI streaming response next to a chat app in the iOS Simulator"><figcaption><p>Capture OpenAI Endpoints</p></figcaption></figure>

### 2.2 Connection Log

* **Connection Log** shows connection info for the selected request, including DNS lookups, TCP connections, TLS negotiation, certificates, and HTTP headers.
* Click **+** in the Request tab bar. Under **Request**, check **Connection Log** to show it or uncheck it to hide it.
* The tab appears next to **Summary** in the Request panel. It is enabled by default, and Proxyman remembers your choice.
* See the [HTTP/2 guide](http2.md) for a sample log, or the [Connection Log guide](connection-log.md) for all fields.

<!-- IMAGE PLACEHOLDER: Custom Previewer Tab with Connection Log checked under Request. -->

## 3. ⚡️ Advanced: Create a custom Tab with the Scripting Tool

* ✅ Show your own data on your tab
* Useful when you want to decode your body or show part of the body in your own tab

### How to use

1. Click the "+" button on the Request/Response tab bar, or go to **Tools** → **Custom Previewer Tab…**
2. Click the **Add Custom Tabs** button
3. Select the Request or Response panel and set a name for your tab

<figure><img src="../.gitbook/assets/Screenshot 2024-06-27 at 15.01.51.png" alt="Proxyman Create new Custom Tab sheet with Tab Location and Custom Tab Name fields"><figcaption><p>Create a new custom tab</p></figcaption></figure>

4. Click the "..." button to show the JavaScript code

<figure><img src="../.gitbook/assets/343035426-24d2901d-10e3-4fa0-a472-579df7385358.jpg" alt="Proxyman Custom Previewer Tab window with a new json tab and a popover with sample JavaScript code"><figcaption><p>Show the Javascript Code</p></figcaption></figure>

5. Open **Scripting** → **Script List…**, create a new [script](../scripting/script.md), and use this code to display your own data

<figure><img src="../.gitbook/assets/343035431-1a336092-5c50-4e23-afbb-9a41f9679bb9.jpg" alt="Proxyman Script Editor setting customPreviewerTabs values in onRequest and onResponse"><figcaption><p>Write your code to display data</p></figcaption></figure>

6. Done

<figure><img src="../.gitbook/assets/343035436-dc7e6346-9ac6-4601-b07a-8294de2c4a02.jpg" alt="Proxyman showing custom body and json tabs filled with data from a script"><figcaption><p>Display your data on a new tab</p></figcaption></figure>

## 4. Examples

### Force render JSON TreeView

Proxyman supports JSON Tree View for better visualization

![Proxyman Response Treeview tab showing JSON keys, types and values](../.gitbook/assets/JSON.png)

You can show or hide a column by right-clicking the column header

![Right-click menu on the Treeview column header to show or hide the Key, Type and Value columns](../.gitbook/assets/JSON_Col.png)

### Force render HTML Page

![Proxyman Response Webview tab rendering an HTML page](../.gitbook/assets/Screen_Shot_2020-07-14_at_10_19_51.png)

### Beautify the Javascript files

![Minified JavaScript in Proxyman next to the same file beautified in the JS tab](../.gitbook/assets/Screen_Shot_2020-07-12_at_08_40_52.png)

## Learn more

* [Debug OpenAI Server-Sent Events with Proxyman](https://proxyman.com/posts/debug-server-sent-event-openapi-endpoint-with-proxyman)
* [Preview multipart/form-data bodies from HTTP requests and responses](https://proxyman.com/posts/2021-06-24-preview-multipart-formdata)
