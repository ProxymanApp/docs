---
description: >-
  Step-by-step tutorial: use Proxyman for iOS Breakpoint to pause traffic on
  your iPhone and edit the URL, method, headers, body and status code.
---

# Breakpoint for iOS Tutorial

## Modify HTTP(s) Request & Response on your iPhone with Proxyman Breakpoint

Since version 2.0.0, Proxyman for iOS lets you change request and response data on the fly, without changing any logic in your app.

<figure><img src="../../.gitbook/assets/1 (1).png" alt="Proxyman for iOS Breakpoint Request Editor with method, URL, header, query and body of a paused POST request"><figcaption><p>Breakpoint Request Editor</p></figcaption></figure>

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

<figure><img src="../../.gitbook/assets/image (5).png" alt="Proxyman for iOS Breakpoint Rules list with a plus button that opens the New Breakpoint Rule form"><figcaption><p>Create a Breakpoint rule manually</p></figcaption></figure>

2. From the "Waiting Breakpoints" screen

* Tap the Waiting Breakpoint icon → **Create Breakpoint Rule**.
* Then fill in the rule (same as the previous option).

<figure><img src="../../.gitbook/assets/image (17).png" alt="Proxyman for iOS empty Waiting Breakpoints screen with a Create Breakpoint Rule button that opens the rule form"><figcaption><p>Create a rule from the Waiting Breakpoints screen</p></figcaption></figure>

3. From the context menu

* Long-press the request → **Add to Breakpoint List**.
* Proxyman fills in all fields of the rule from the selected request.

<figure><img src="../../.gitbook/assets/image (4).png" alt="Proxyman for iOS context menu with Add to Breakpoint List, which opens a rule filled with httpbin.org"><figcaption><p>Create a Breakpoint rule from a request</p></figcaption></figure>

In this example, the Breakpoint rule applies to both requests and responses. Let's make a request to see how it works.

<figure><img src="../../.gitbook/assets/image (8).png" alt="Proxyman for iOS Breakpoint Rules list with one enabled rule for httpbin.org tagged Request and Response"><figcaption><p>The rule applies to both requests and responses</p></figcaption></figure>

## Modify HTTP(s) Requests

When you make a request that matches the URL, Proxyman pauses it and shows that there are waiting breakpoints. On the Home screen, tap the small icon to see the waiting breakpoint list. Then select a breakpoint to start editing the request.

<figure><img src="../../.gitbook/assets/image (3).png" alt="Proxyman for iOS Home screen with the waiting breakpoint icon and the Waiting Breakpoints list with a POST request"><figcaption><p>Open the waiting breakpoint list</p></figcaption></figure>

### Modify URL + Method

You can change the HTTP method, URL, and query. The URL updates when the queries change, and the other way around.

<figure><img src="../../.gitbook/assets/image (18).png" alt="Proxyman for iOS Breakpoint Request Editor with an edited URL query and the HTTP method menu open"><figcaption><p>Modify the URL and HTTP method</p></figcaption></figure>

### Modify Body

If you replace the body with a new data type, Proxyman detects the Content-Type and updates the headers for you.

<figure><img src="../../.gitbook/assets/image (2).png" alt="Proxyman for iOS Edit Body screen loading a file from iCloud and asking to set a new Content-Type header"><figcaption><p>Use a local file as the request body</p></figcaption></figure>

## Execute, abort, continue Breakpoint

When you're happy with the change, execute the request or response from the menu at the top right. To keep the original request, use **Continue**. To cancel it, use **Abort**.

<figure><img src="../../.gitbook/assets/image (6).png" alt="Proxyman for iOS Breakpoint Request Editor menu with Execute, Continue and Abort"><figcaption><p>Execute, continue or abort a breakpoint</p></figcaption></figure>

Since the Breakpoint rule applies to both the request and the response, the response is added to the waiting breakpoint list after you tap **Execute**.

<figure><img src="../../.gitbook/assets/image (1).png" alt="Proxyman for iOS Waiting Breakpoints list with a paused response and the Breakpoint Response Editor"><figcaption><p>Edit the paused response</p></figcaption></figure>

Now you can change the HTTP status code, update headers, or replace the body of the response (the same way as modifying the request).

<figure><img src="../../.gitbook/assets/image (16).png" alt="Proxyman for iOS status code picker and Edit Body menu for a paused response"><figcaption><p>Modify the response status code and body</p></figcaption></figure>

Nicely done! In the flow list, a small blue icon shows that this flow has been modified.

<figure><img src="../../.gitbook/assets/image (7).png" alt="Proxyman for iOS Execute action on a response next to the flow list with a blue modified icon"><figcaption><p>A blue icon marks the modified flow</p></figcaption></figure>

Both the request and the response have been updated as expected.

<figure><img src="../../.gitbook/assets/image (9).png" alt="Proxyman for iOS request details executed by Breakpoint and the new response body"><figcaption><p>The request and response are modified by Breakpoint</p></figcaption></figure>

**NOTES**:

* When you create a new rule, both the Breakpoint tool and the rule are enabled by default. You can switch them on or off as needed.
* Make sure the VPN, the Breakpoint tool, and the Breakpoint rule are all enabled so that Breakpoint can work.
* If the first rule matches the request or response, other rules are not applied.
* While you edit the request, the Response tab is disabled. While you edit the response, the Request tab is read-only.

## What's next

Breakpoint lets you modify the request and response on the fly, but it needs a lot of manual work. To automate it, check out the [Map Local for iOS tutorial](map-local-for-ios-tutorial.md) to map a local file as a response automatically.
