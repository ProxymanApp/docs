---
description: >-
  Solution to capture HTTP/HTTPS Requests/Responses from Python, NodeJS, Ruby or
  Golang with Proxyman
---

# I could not see any HTTP traffic from my NodeJS, Python, or Ruby scripts

## 1. Problem:

* I have NodeJS, Ruby, Python, or Golang scripts/servers, which make an internal HTTP/HTTPS request -> However, I don't see any traffic from the Proxyman app.

For example:&#x20;

* NodeJS: I'm using the [axios](https://github.com/axios/axios) library (NodeJS) to call a RESTFUL API from my production server (e.g. https://mycompany.com/v1/data). However, there is no traffic recorded from the Proxyman app.
* I'm using net/http from Golang, but no requests appear on Proxyman
* ... so all

## 2. New Automatic Solution (v4.7.0 or later) ✅

Proxyman v4.7.0 or later can capture HTTP/HTTPS traffic from Python/Ruby/NodeJS/Golang with 1-click.

* 1-click solution: No need to manually set HTTP Proxy config or trust the self-signed certificate.
* Support many network libraries from NodeJS, Python, Ruby, and Golang

### 2.1 How to use:

1. Open Proxyman -> Setup Menu -> Automatic Setup
2. Click on "Open New Terminal"

<figure><img src="../.gitbook/assets/Screenshot 2025-03-18 at 10.54.37.jpg" alt=""><figcaption><p>Start pre-configured Terminal</p></figcaption></figure>



3. Accept the Apple Script permission prompt if needed
4. The New Terminal app is launched -> You can start your Python Backend Server, or Run scripts => Proxyman automatically captures all traffic.

<figure><img src="../.gitbook/assets/CleanShot 2025-03-18 at 09.56.44@2x.jpg" alt=""><figcaption><p>Capture HTTPS traffic from Ruby, Python, NodeJS and Golang Server/Scripts</p></figcaption></figure>

3. Done ✅

## 3. Other Problems

### 3.1 I could not see any `fetch()`request from NextJS - Server Side Component

* Solution on this blog: [https://proxyman.com/posts/2024-06-10-Capture-HTTPS-From-NextJS-Server-Components](https://proxyman.com/posts/2024-06-10-Capture-HTTPS-From-NextJS-Server-Components)

