---
description: >-
  NodeJS, Python, Ruby or Golang requests not showing in Proxyman? Capture them
  with Automatic Setup in one click, or with Network Extension on macOS 26.
---

# I could not see any HTTP traffic from my NodeJS, Python, or Ruby scripts

## 1. Problem

* I have NodeJS, Ruby, Python, or Golang scripts or servers that make HTTP/HTTPS requests. However, I don't see any traffic in the Proxyman app.

For example:&#x20;

* NodeJS: I'm using the [axios](https://github.com/axios/axios) library to call a REST API on my production server (for example https://mycompany.com/v1/data). However, Proxyman doesn't record any traffic.
* I'm using net/http in Golang, but no requests appear in Proxyman.
* ... and so on.

{% hint style="info" %}
Try [Network Extension](../advanced-features/network-extension.md) to capture HTTP/HTTPS requests from scripts running on your Mac without setting a proxy in each library. For SSL errors, use [Automatic Setup](../automatic-setup/automatic-setup.md) to set up certificate trust for supported libraries.

Network Extension is BETA and requires Proxyman PRO on macOS 26 or later.
{% endhint %}

## 2. New Automatic Solution (v4.7.0 or later) ✅

Proxyman v4.7.0 or later can capture HTTP/HTTPS traffic from Python, Ruby, NodeJS and Golang with one click.

* One-click solution: no need to set the HTTP proxy or trust the self-signed certificate by hand.
* Supports many network libraries for NodeJS, Python, Ruby, and Golang.

### 2.1 How to use

1. Open Proxyman -> **Setup** menu -> **Automatic Setup…**
2. Click **Open New Terminal…**

<figure><img src="../.gitbook/assets/Screenshot 2025-03-18 at 10.54.37.jpg" alt="Proxyman Automatic Setup window with the Open New Terminal button and supported Golang libraries"><figcaption><p>Start a pre-configured Terminal</p></figcaption></figure>

3. Accept the AppleScript permission prompt if needed.
4. A new Terminal window opens. Start your Python backend server or run your scripts there. Proxyman captures all their traffic.

<figure><img src="../.gitbook/assets/CleanShot 2025-03-18 at 09.56.44@2x.jpg" alt="Proxyman capturing HTTPS requests from a Go script using net/http, fasthttp, resty and gorequest"><figcaption><p>Capture HTTPS traffic from Ruby, Python, NodeJS and Golang servers and scripts</p></figcaption></figure>

5. Done ✅

## 3. Other Problems

### 3.1 I can't see any `fetch()` request from a NextJS Server Component

* See this blog post: [Capture HTTPS from NextJS Server Components](https://proxyman.com/posts/2024-06-10-Capture-HTTPS-From-NextJS-Server-Components)

## Learn more

* [Capture HTTP/HTTPS requests from Axios in NodeJS](https://proxyman.com/posts/2023-05-14-Capture-HTTP-HTTPS-Request-From-Axios-NodeJS)
* [Capture HTTP/HTTPS requests from Ruby net/http](https://proxyman.com/posts/2023-05-09-Capture-HTTP-HTTPS-Request-Response-From-Ruby-Net-HTTP-library)
* [Capture HTTPS traffic from Python Requests and HTTPX](https://proxyman.com/posts/2025-01-29-How-To-Capture-HTTPS-Traffic-From-Python-Requests-httpx)

