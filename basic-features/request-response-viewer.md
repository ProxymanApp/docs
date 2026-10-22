---
description: >-
  Inspect requests and responses in Proxyman with Header, Cookies, Query, Body,
  Raw and JSON Tree View tabs, and arrange the panels to fit your work.
---

# Request / Response Previewer

After installing the [Certificate](../debug-devices/macos.md) and enabling [SSL Proxying](ssl-proxying.md) on domains or apps, your network traffic shows up immediately in the Proxyman window. The window has three main areas:

* The Source List on the left panel&#x20;
* The Flow List on the middle panel&#x20;
* The Flow Content on the right panel

![Proxyman main window with the Source List, Flow List and Flow Content areas labeled](../.gitbook/assets/01.png)

## Body Content Previewer

Depending on the content of the request or response, Proxyman automatically shows it in separate tabs:

* **Header**: All headers (key-value table)
* **Cookies**: The **Cookie** header of the request
* **Set-Cookie**: The Set-Cookie header of the response
* **Auth**: The **Authorization** header
* **Body**: The body of the message. Proxyman automatically formats and beautifies the body based on the **Content-Type**, such as JSON, PNG, GIF, Raw Data, ...
* **Query**: All query parameters of the request
* **Raw**: The raw HTTP message
* [Protobuf](../advanced-features/protobuf.md) Message
* MessagePack
* [Multipart/form-data](multipart-form-data-previewer.md)

## Custom Previewer Tab

You can choose which previewer tabs you would like to see:

* Custom tabs stay on the Request/Response panel
* Proxyman tries to decode and beautify the content in the selected format

{% content-ref url="custom-previewer-tab.md" %}
[custom-previewer-tab.md](custom-previewer-tab.md)
{% endcontent-ref %}

![Proxyman Custom Previewer Tab window with format checkboxes for the Request and Response panels](<../.gitbook/assets/Screen Shot 2021-06-25 at 09.39.55.png>)

## Layout mode

There are two ways to arrange the Request / Response panels: [Vertical or Horizontal layout](horizontal-vertical-layout.md).

![Request Raw tab and Response JSON body side by side in Proxyman](../.gitbook/assets/http\_response\_vertical.png)

![Proxyman request list with the Request and Response panels below it in Horizontal layout](<../.gitbook/assets/Screen Shot 2020-04-25 at 16.21.34.png>)

![Proxyman request list with the Request and Response panels on the right in Vertical layout](<../.gitbook/assets/Screen Shot 2020-04-25 at 16.21.55.png>)

## Customize Workspace

Use the layout buttons in the top-right corner of the app to arrange the content the way you like:

1. Collapse/Expand the Source List panel&#x20;
2. Open the Request/Response panel in a new window
3. Show the Request/Response panel in Horizontal layout
4. Show the Request/Response panel in Vertical layout

![Proxyman toolbar buttons for the detachable window, Source List, Horizontal and Vertical layout](../.gitbook/assets/02.png)

## Shortcuts

All sections support **Copy (⌘C)** and multiple selection.

![Proxyman request Header tab with several rows selected and a Copy ⌘C context menu](<../.gitbook/assets/Screen Shot 2019-08-17 at 10.04.36.png>)

Read more in our [Proxyman keyboard shortcuts](https://proxyman.com/posts/2019-08-20-Useful-shortcuts-that-boost-your-productivity) blog post.

## **Body Previewer**&#x20;

The Body previewer automatically beautifies the content and offers handy extra features:

* **Tree View**: Show the JSON in Tree View mode
* **Hex**: Show the body in Hex format
* **Export only body**: Export the body content to a file. Useful for raw or binary data
* **Open With**: Open the body content in your favorite editor. **Sublime Text** is mine 😍

![Proxyman response Body menu with Tree View, JSON, Open with editor and Export options](../.gitbook/assets/body\_previewer.png)

## JSON Tree View mode

Proxyman has a native JSON Tree View mode for JSON bodies. It lets you:

* Search JSON by [JSON Path](jsonpaths.md)
* Copy a JSON node, like in Google Chrome DevTools

![Proxyman JSON Treeview tab with a Copy Value menu and the JSON Path search field](<../.gitbook/assets/Screen Shot 2021-10-15 at 16.14.44.png>)

## Learn more

* [Preview multipart/form-data bodies from HTTP requests and responses](https://proxyman.com/posts/2021-06-24-preview-multipart-formdata)
