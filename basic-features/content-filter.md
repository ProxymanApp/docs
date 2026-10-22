---
description: >-
  Use the Proxyman Content Filter to find requests fast by type, status code,
  URL, header, body and more, with contains, wildcard and regex matching.
---

# Content Filter

Proxyman offers the Primary and Secondary Filters to quickly find the requests or responses you're looking for.

{% hint style="info" %}
**⌘F**: Open the Filter Bar

**ESC**: Close the Filter Bar
{% endhint %}

![Proxyman filter bar with HTTP, JSON, Form, 2xx and 4xx filters selected at the same time](../.gitbook/assets/111282473-9e95ab00-8670-11eb-8d05-6e2c641a82bb.png)

![Proxyman filter bar with several content types and status codes selected by holding ⌘ and clicking](../.gitbook/assets/Screen\_Shot\_2021-03-22\_at\_22\_29\_07.png)

![Proxyman Secondary Filter menu listing URL, Query String, Header, Body, Method, Status Code, Comment and Color](<../.gitbook/assets/CleanShot 2020-11-17 at 08.31.48@2x.png>)

![Proxyman filter matching menu with Contains, Not Contains, Start With, End With, Equal, Not Equal and Regex](<../.gitbook/assets/CleanShot 2020-11-17 at 08.31.52@2x.png>)

## Primary Filter

| Filter    | Description                                                     |
| --------- | --------------------------------------------------------------- |
| All       | All Requests and Responses                                      |
| HTTP      | Only HTTP                                                       |
| HTTPS     | Only HTTPS                                                      |
| WebSocket | Only WebSocket and Secure WebSocket                             |
| JSON      | Content-Type is application/json or JSON contents               |
| Form      | Only Form Body in Request / Response                            |
| XML       | Only XML                                                        |
| JS        | Only JavaScript content                                         |
| CSS       | Only CSS content                                                |
| GraphQL   | GraphQL requests (the URL contains `/graphql`)                  |
| Document  | Document content: HTML, ...                                     |
| Media     | Image, audio and video content: PNG, JPG, GIF, ...              |
| Other     | Other content that doesn't match any of the above               |
| h1        | Only HTTP/1.x requests                                          |
| h2        | Only [HTTP/2](http2.md) requests                                |

## Status Filters

| Filter | Description                  |
| ------ | ---------------------------- |
| 1xx    | Status codes from 100 to 199 |
| 2xx    | Status codes from 200 to 299 |
| 3xx    | Status codes from 300 to 399 |
| 4xx    | Status codes from 400 to 499 |
| 5xx    | Status codes 500 and above   |

{% hint style="info" %}
Hold the ⌘ key and click to select multiple types.
{% endhint %}

## Secondary Filter

### Content

* URL
* Host
* Query String
* Request Header
* Response Header
* Request Body
* Response Body
* Method
* Status Code
* Duration (ms)
* Request Body Size (KB)
* Response Body Size (KB)
* GraphQL
* Client
* IP Address
* Comment
* Color

### Matching

* Contains
* Not Contains
* Start With
* End With
* Equal
* Not Equal
* `<` (less than, for numbers)
* `>=` (greater than or equal, for numbers)
* Match Wildcard
* Not Match Wildcard
* Match Regex
* Not Match Regex

## Header, Query, Auth, Form Filter

From Proxyman 2.34.0+, you can quickly filter the Header, Query, Auth, and Form content of the selected request and response.

1. Click the view (e.g. the Header tab of the Request)
2. Press ⌘F or right-click → **Show Filter** to open the filter

![Proxyman Request Header tab filtered by the word json, showing only matching headers](../.gitbook/assets/Screen\_Shot\_2021-10-14\_at\_22\_59\_20.png)

## Learn more

* [Use Multiple Filters to find HTTP requests faster](https://proxyman.com/posts/2021-04-08-Use_Multiple_Filters)
