---
description: >-
  Step-by-step tutorial: use Proxyman for iOS Breakpoint to pause traffic on
  your iPhone and edit the URL, method, headers, body and status code.
---

# Breakpoint for iOS Tutorial

## Modify HTTP(s) Request & Response on your iPhone with Proxyman Breakpoint

Since version 2.0.0, Proxyman for iOS lets you change request and response data on the fly, without changing any logic in your app.

This short tutorial shows how to modify HTTP(s) requests and responses on iOS devices with the Proxyman Breakpoint tool. For example:

* Modify the request URL (including the scheme, host, path, port) and HTTP method
* Modify HTTP headers of the request or response
* Modify the query of a request
* Modify the HTTP body of the request or response
* Modify the response HTTP status code

## Prerequisites

* Download the latest version of Proxyman from the App Store: [https://apps.apple.com/us/app/proxyman/id1551292695](https://apps.apple.com/us/app/proxyman/id1551292695)
* Install and trust the Proxyman certificate on your iOS device. If you're new to Proxyman, follow [Capture and inspect HTTPS traffic from iPhone](https://proxyman.com/posts/2021-10-17-Getting-Started-With-Proxyman-For-iOS) to start capturing HTTP traffic on your iPhone.

## Create Breakpoint Rules

There are 3 ways to create a Breakpoint rule:

1. From the More tab

* Go to the **More** tab → **Breakpoint** → tap the **+** button.
* Fill in the fields for the rule: Title, Method, Matching URL, and whether to include subpaths.
* Choose whether the rule applies to requests, responses, or both.

2. From the "Waiting Breakpoints" screen

* Tap the Waiting Breakpoint icon → **Create Breakpoint Rule**.
* Then fill in the rule (same as the previous option).

3. From the context menu

* Long-press the request → **Add to Breakpoint List**.
* Proxyman fills in all fields of the rule from the selected request.

<figure><img src="../../.gitbook/assets/image (4).png" alt="Proxyman for iOS context menu with Add to Breakpoint List, which opens a rule filled with httpbin.org"><figcaption><p>Create a Breakpoint rule from a request</p></figcaption></figure>

In this example, the Breakpoint rule applies to both requests and responses. Let's make a request to see how it works.

## Modify HTTP(s) Requests

When you make a request that matches the URL, Proxyman pauses it and shows that there are waiting breakpoints. On the Home screen, tap the small icon to see the waiting breakpoint list. Then select a breakpoint to start editing the request.

### Modify URL + Method

You can change the HTTP method, URL, and query. The URL updates when the queries change, and the other way around.

<figure><img src="../../.gitbook/assets/image (18).png" alt="Proxyman for iOS Breakpoint Request Editor with an edited URL query and the HTTP method menu open"><figcaption><p>Modify the URL and HTTP method</p></figcaption></figure>

### Modify Body

If you replace the body with a new data type, Proxyman detects the Content-Type and updates the headers for you.

## Execute, abort, continue Breakpoint

When you're happy with the change, execute the request or response from the menu at the top right. To keep the original request, use **Continue**. To cancel it, use **Abort**.

Since the Breakpoint rule applies to both the request and the response, the response is added to the waiting breakpoint list after you tap **Execute**.

Now you can change the HTTP status code, update headers, or replace the body of the response (the same way as modifying the request).

Nicely done! In the flow list, a small blue icon shows that this flow has been modified.

Both the request and the response have been updated as expected.

<figure><img src="../../.gitbook/assets/image (9).png" alt="Proxyman for iOS request details executed by Breakpoint and the new response body"><figcaption><p>The request and response are modified by Breakpoint</p></figcaption></figure>

**NOTES**:

* When you create a new rule, both the Breakpoint tool and the rule are enabled by default. You can switch them on or off as needed.
* Make sure the VPN, the Breakpoint tool, and the Breakpoint rule are all enabled so that Breakpoint can work.
* If the first rule matches the request or response, other rules are not applied.
* While you edit the request, the Response tab is disabled. While you edit the response, the Request tab is read-only.

## What's next

Breakpoint lets you modify the request and response on the fly, but it needs a lot of manual work. To automate it, check out the [Map Local for iOS tutorial](map-local-for-ios-tutorial.md) to map a local file as a response automatically.
