---
description: >-
  Solution to capture HTTP/HTTPS Requests/Responses from Python, NodeJS and Ruby
  with Proxyman
---

# I could not see any HTTP traffic from my NodeJS, Python, or Ruby scripts

## 1. Problem:

* I have NodeJS, Ruby, or Python scripts, which make an HTTP/HTTPS request to an external server -> However, I don't see any traffic from the Proxyman app.

For example: I'm using [axios](https://github.com/axios/axios) library (NodeJS) to call a RESTFUL API from my production server (e.g https://mycompany.com/v1/data). However, there is no traffic recorded from Proxyman app.



## 2. New Automatic Solution (v4.7.0 or later) ✅

Proxyman v4.7.0 or later can capture HTTP/HTTPS traffic from Python with 1-click.

* 1-click solution: No need to manually set HTTP Proxy config or trust the self-signed certificate.
* Support many network library from NodeJS, Python and Ruby.

### How to use:

1. Open Proxyman -> Setup Menu -> Automatic Setup
2. Click on "Open New Terminal"
3. Accept the Apple Script permission prompt if needed
4. The New Terminal app is launched -> You can start your Python Backend Server, or Run scripts => Proxyman automatically captures all traffic.
5. Done ✅

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.18.19@2x.jpg" alt=""><figcaption></figcaption></figure>
