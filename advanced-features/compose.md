---
description: >-
  Make new HTTPS Requests to your server, and inspect the HTTPS Response. It's a
  simple version of Postman
---

# Compose new Request

## 1. What's it?

"Compose new Request" tool is a handy tool to help developers:

* Compose an HTTP/HTTPS Request and send it to your service. It's similar to Paw, Insomnia, and Postman.
* Quickly test your APIs without depending on your app client.
* Support Header, Query, URL, Form, JSON Body
* Support Raw Message
* Support multipart body
* Preset template: Empty Request, GET Request, Post Request with JSON or Form.

{% hint style="info" %}
You can reuse your request data for new requests. Please check out the [Edit & Repeat](edit-and-repeat.md) page.
{% endhint %}

<figure><img src="../.gitbook/assets/Screenshot 2025-09-05 at 21.01.54.png" alt=""><figcaption><p>Make a HTTPS Requests with Proxyman</p></figcaption></figure>

## 2. How to use

You can open the tool by either:

* Click on the Compose button on the main navigation bar
* Tools -> Compose

![Open the Compose Tool](../.gitbook/assets/Screen_Shot_2022-06-23_at_15_03_44.jpg)

1. Enter the URL
2. Select HTTP Method
3. Modify the Header, Param, Body, Raw Message
4. Click the Send button.

![Compose JSON Body](../.gitbook/assets/Screen_Shot_2022-06-23_at_15_07_35.jpg) ![Using Raw Message](../.gitbook/assets/Screen_Shot_2022-06-23_at_15_08_10.jpg)

## 3. Template

Proxyman also supports a few request templates.

* GET with Query
* Post with JSON
* Post with Form
* Post with multiparts
* Import from cURL

![Use preset template](<../.gitbook/assets/Screenshot 2025-02-01 at 10.45.59 PM.jpg>)

## 4. Import from cURL

You can import your cURL, which you can copy from a Network Tab in Google Chrome and make a request with the Compose Tool.

<figure><img src="../.gitbook/assets/Screenshot 2025-02-01 at 10.42.21 PM.jpg" alt=""><figcaption><p>import cURL</p></figcaption></figure>

{% hint style="success" %}
You can simply paste your cURL to the URL Text View, Proxyman will tries to parse your cURL
{% endhint %}

## 5. History Request

From Proxyman macOS 5.24.0, Proxyman will store your requests/responses in the History List.

* ✅ Useful to preview your previous Request/Response

<figure><img src="../.gitbook/assets/Screenshot 2025-08-25 at 14.02.04.jpg" alt=""><figcaption><p>Request History in the Compose View</p></figcaption></figure>

## 6. Settings

* **SettingsRequest Timeout**: In Setting -> Tools Tab -> Request Timeout: Define a second that the Request will timeout. Use 0 to disable it. Available on Proxyman 4.13.0 or later
