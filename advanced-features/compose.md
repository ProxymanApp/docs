# Compose new Request

### 1. What's it?

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

### 2. How to use

You can open the tool by either:

* Click on Compose button on the main navigation bar
* Tools -> Compose

![Open the Compose Tool](../.gitbook/assets/Screen\_Shot\_2022-06-23\_at\_15\_03\_44.jpg)

1. Enter the URL
2. Select HTTP Method
3. Modify the Header, Param, Body, Raw Message
4. Click Send button.

![Compose JSON Body](../.gitbook/assets/Screen\_Shot\_2022-06-23\_at\_15\_07\_35.jpg) ![Using Raw Message](../.gitbook/assets/Screen\_Shot\_2022-06-23\_at\_15\_08\_10.jpg)

### 3. Template

Proxyman also supports few request templates.

![Use preset template](../.gitbook/assets/174536860-262235dc-a903-48a8-86af-97bceacb45de.png)

### 4. Settings

* **Request Timeout**: In Setting -> Tools Tab -> Request Timeout: Define a second that the Request will timeout. Use 0 to disable it. Available on Proxyman 4.13.0 or later
