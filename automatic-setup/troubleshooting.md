---
description: >-
  Fix common Proxyman Automatic Setup and Manual Setup problems: missing traffic
  from NodeJS, Python or Ruby, SSL errors, and localhost requests.
---

# Troubleshooting

## 1. Automatic Setup does not capture any HTTP Traffic from my new networking library

Proxyman supports the following libraries:

* **NodeJS**: Axios, got, superagent, fetch, and node-fetch
* **Python**: http, https, aiohttp, requests
* **Ruby**: http, net/http, net/https, faraday, and httparty

\-> If you're using a new library and Proxyman Automatic Setup doesn't capture your HTTP/HTTPS traffic, please [create a new ticket on GitHub](https://github.com/ProxymanApp/Proxyman/issues) to request support for your library.

{% hint style="info" %}
If your library running on your Mac ignores proxy settings, try [Network Extension](../advanced-features/network-extension.md). It captures supported HTTP/HTTPS traffic without relying on Automatic Setup's proxy configuration. Certificate trust is still required for HTTPS.

Network Extension is BETA and requires Proxyman PRO on macOS 26 or later.
{% endhint %}

## 2. I get SSL Errors from my NodeJS, Ruby, Python script

\-> Make sure you've installed and trusted the certificate on macOS. Open the **Certificate** menu -> **Install Certificate on this Mac…**.

\-> If the error still happens, there may be a bug in the Automatic Setup feature. Please [create a new ticket on GitHub](https://github.com/ProxymanApp/Proxyman/issues) and let us know.

## 3. Proxyman could not record any traffic from my local server, e.g http://localhost:3000

By default, traffic from http://localhost:3000 doesn't go through the system proxy. Therefore, Proxyman can't capture it.

Follow [I could not see any requests from my localhost server](../troubleshooting/couldnt-see-any-request-from-localhost-server.md) to fix it.
