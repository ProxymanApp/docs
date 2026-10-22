---
description: >-
  Step-by-step tutorial: mock HTTP/HTTPS responses on your iPhone with Proxyman
  for iOS Map Local and change the status code, headers and body.
---

# Map Local for iOS Tutorial

## Manipulate HTTP(s) responses on iPhone with Proxyman Map Local

Since version 2.0.0, Proxyman for iOS has the Map Local tool. It lets you use the content of a local file as the response to requests that match your rules.

Map Local helps you develop faster. You can quickly test edge cases without changing the data on your server. It's also a must-have tool for QA and developers who want to test the app's behavior with different responses. Some testing scenarios:

* Define a response and use it for matching requests.
* Quickly try new parameters in responses.
* Test the app's behavior with different parameters in the responses.
* Test the UI layout with unusual content.
* Quickly reproduce a bug with specific parameters in responses.
* Mock an API with a local file. It's useful when you want to try test APIs that are not in production yet.

## Prerequisites

* Download the latest version of Proxyman from the App Store: [https://apps.apple.com/us/app/proxyman/id1551292695](https://apps.apple.com/us/app/proxyman/id1551292695)
* Install and trust the Proxyman certificate on your iOS device. If you're new to Proxyman, follow [Capture and inspect HTTPS traffic from iPhone](https://proxyman.com/posts/2021-10-17-Getting-Started-With-Proxyman-For-iOS) to start capturing HTTP traffic on your iPhone.

## Create Map Local Rules

There are 2 ways to create a Map Local rule:

1. From the More tab

* Go to the **More** tab → **Map Local** → tap the **+** button.
* Fill in the fields for the rule: Name, URL, Method, and whether to include subpaths.

2. From the context menu

* Long-press the request → **Add to Map Local**.
* Proxyman fills in all fields of the rule from the selected request.

<figure><img src="../../.gitbook/assets/image (14).png" alt="Proxyman for iOS context menu with Add to Map Local, which opens a Map Local Editor filled from the request"><figcaption><p>Create a Map Local rule from a request</p></figcaption></figure>

### Modify Header, Status Code and Body

In the Map Local Editor, you can change the headers, status code, and body. If you replace the body with a new data type, Proxyman detects the Content-Type and updates the headers for you.

## Manipulate Response with Map Local Tool

<figure><img src="../../.gitbook/assets/image (12).png" alt="Proxyman for iOS Map Local Editor with status 201 Created next to the enabled Map Local rule list"><figcaption><p>Enable Map Local and the rule</p></figcaption></figure>

You're all set. Make another request to see how it works.

If the URL of an incoming request matches a **pre-defined matching rule** and the local file is valid, Proxyman replaces the response body of that request with the content of the local file.

If a request doesn't match any rule, the response from the server stays the same.

<figure><img src="../../.gitbook/assets/image (13).png" alt="Proxyman for iOS flow list, request details executed by Map Local, and the response body replaced by a local file"><figcaption><p>The response is modified by Map Local</p></figcaption></figure>

Nicely done! In the flow list, a small blue icon shows that this flow has been modified. The response content has been replaced with the local file.

## What's next

Map Local lets you try different responses to test the layout or content on your device. But it can only modify the response. If you'd like to modify the request too, check out the [Breakpoint for iOS tutorial](breakpoint-for-ios-tutorial.md). Breakpoint lets you change both the request and the response on the fly without changing any logic in your app.
