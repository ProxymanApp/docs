---
description: Make a Restful Requests to your server, and inspect the HTTPS Response
---

# Compose new Request

## 1. What's it?

Compose a new Request is a handy tool to help developers:

* Compose an HTTP/HTTPS Request and send it to your service. It's similar to Paw, Insomnia, and Postman.
* Quickly test your APIs without depending on your app client.
* Support Header, Query, URL, Form, JSON Body
* Support Raw Message
* Preset template: Empty Request, GET Request, Post Request with JSON or Form.

{% hint style="info" %}
You can reuse your request data for new requests. Please check out the [Edit & Repeat](edit-and-repeat.md) page.
{% endhint %}

![Compose new request and inspect the response](../.gitbook/assets/174536780-6ced0dc3-df59-4c51-a1a5-dc72cb30140f.jpeg)

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

## 5. Settings

* **Request Timeout**: In Setting -> Tools Tab -> Request Timeout: Define a second that the Request will timeout. Use 0 to disable it. Available on Proxyman 4.13.0 or later
