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

## 2. How to use

You can open the tool by either:

* Click the Compose button on the main toolbar
* **Tools** -> **Compose Request…** (⌥⌘C)

1. Enter the URL
2. Select the HTTP Method
3. Modify the Header, Query, Body, or Raw Message
4. Click the **Send** button.

<figure><img src="../.gitbook/assets/proxyman-compose-json-body.jpg" alt="Proxyman Compose window sending a POST request with a JSON body and getting a 201 Created JSON response"><figcaption><p>Send a POST request with a JSON body</p></figcaption></figure>

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

<figure><img src="../.gitbook/assets/proxyman-compose-template-menu.jpg" alt="Proxyman Compose Template menu with presets such as QUERY with Body and WebSocket, and Import from cURL highlighted"><figcaption><p>Compose templates</p></figcaption></figure>

## 4. Import from cURL

You can import a cURL command, for example one copied from the Network tab in Google Chrome, and send it with the Compose tool. Click **Template** -> **Import from cURL…**.

{% hint style="success" %}
You can also paste your cURL command into the URL field. Proxyman tries to parse it.
{% endhint %}

## 5. History Request

From Proxyman macOS 5.24.0, Proxyman stores your requests and responses in the **History** list.

* ✅ Useful to preview your previous Request/Response

## 6. Settings

* **Request Timeout**: Click the **⋯** button at the bottom of the Compose window -> **Request Timeout**. Pick 15, 30, or 60 seconds, a custom value, or **0 (No Timeout)**. The same timeout applies to [repeated requests](repeat.md). Available on Proxyman 4.13.0 or later.

<figure><img src="../.gitbook/assets/proxyman-compose-request-timeout.jpg" alt="Proxyman Compose ⋯ menu with Request Timeout options 15, 30, 60 seconds, 0 (No Timeout), Custom..."><figcaption><p>Set the request timeout</p></figcaption></figure>

## Learn more

* [Proxyman now supports the HTTP QUERY method](https://proxyman.com/posts/2026-07-11-Proxyman-now-supports-HTTP-QUERY-method)
