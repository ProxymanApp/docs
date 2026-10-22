---
description: >-
  Use Proxyman Compose to build and send HTTP or HTTPS requests to your API,
  import cURL commands, and inspect the response, like a simple Postman.
---

# Compose new Request

## 1. What's it?

The Compose tool helps developers:

* Compose an HTTP/HTTPS request and send it to your service. It's similar to Paw, Insomnia, and Postman.
* Quickly test your APIs without your client app.
* Supports Header, Query, URL, Form, and JSON Body.
* Supports Raw Message.
* Supports multipart body.
* Preset templates, such as Empty Request, GET with Query, and POST with JSON or Form.

{% hint style="info" %}
You can reuse your request data for new requests. Please check out the [Edit & Repeat](edit-and-repeat.md) page.
{% endhint %}

<figure><img src="../.gitbook/assets/Screenshot 2025-09-05 at 21.01.54.png" alt="Proxyman Compose window sending a POST request to httpbin.proxyman.app with a 200 OK JSON response"><figcaption><p>Make an HTTPS request with Proxyman</p></figcaption></figure>

## 2. How to use

You can open the tool by either:

* Click the Compose button on the main toolbar
* **Tools** -> **Compose Request…** (⌥⌘C)

![Compose button in the Proxyman main toolbar](../.gitbook/assets/Screen_Shot_2022-06-23_at_15_03_44.jpg)

1. Enter the URL
2. Select the HTTP Method
3. Modify the Header, Query, Body, or Raw Message
4. Click the **Send** button.

![Proxyman Compose window with a JSON request body and the JSON response](../.gitbook/assets/Screen_Shot_2022-06-23_at_15_07_35.jpg) ![Proxyman Compose Raw tab with a raw HTTP request message](../.gitbook/assets/Screen_Shot_2022-06-23_at_15_08_10.jpg)

## 3. Template

Click the **Template** button at the bottom of the Compose window to start from a preset:

* Empty Request
* GET with Query
* QUERY with Body
* POST with JSON
* POST with Form
* POST with Multiparts
* WebSocket
* Import from cURL…

![Proxyman Compose Template menu with request presets and Import from cURL](<../.gitbook/assets/Screenshot 2025-02-01 at 10.45.59 PM.jpg>)

## 4. Import from cURL

You can import a cURL command, for example one copied from the Network tab in Google Chrome, and send it with the Compose tool. Click **Template** -> **Import from cURL…**.

<figure><img src="../.gitbook/assets/Screenshot 2025-02-01 at 10.42.21 PM.jpg" alt="Proxyman Compose window with the Template menu open and Import from cURL highlighted"><figcaption><p>Import cURL</p></figcaption></figure>

{% hint style="success" %}
You can also paste your cURL command into the URL field. Proxyman tries to parse it.
{% endhint %}

## 5. History Request

From Proxyman macOS 5.24.0, Proxyman stores your requests and responses in the **History** list.

* ✅ Useful to preview your previous Request/Response

<figure><img src="../.gitbook/assets/Screenshot 2025-08-25 at 14.02.04.jpg" alt="Proxyman Compose History menu listing recent requests with status codes and times"><figcaption><p>Request History in the Compose View</p></figcaption></figure>

## 6. Settings

* **Request Timeout**: Click the **⋯** button at the bottom of the Compose window -> **Request Timeout**. Pick 15, 30, or 60 seconds, a custom value, or **0 (No Timeout)**. The same timeout applies to [repeated requests](repeat.md). Available on Proxyman 4.13.0 or later.

## Learn more

* [Proxyman now supports the HTTP QUERY method](https://proxyman.com/posts/2026-07-11-Proxyman-now-supports-HTTP-QUERY-method)
