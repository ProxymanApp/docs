---
description: All problems and solutions when you Automatic/Manual Setup
---

# Troubleshooting

### 1. Automatic Setup does not capture any HTTP Traffic from my new networking library

Proxyman supports the following libraries:

* **NodeJS**: Axios, got, superagent, fetch, and node-fetch
* **Python**: http, https, aiohttp, requests
* **Ruby**: http, net/http, net/htps, faraday, and httparty

\-> If you're using a new library and Proxyman Automatic Setup doesn't capture your HTTP/HTTPS traffic, please [create a new ticket](https://github.com/ProxymanApp/Proxyman/issues) to request your library.

### 2. I get SSL Errors from my NodeJS, Ruby, Python script

\-> Make sure you've installed & trusted the certificate on macOS. You can easily do it by opening the Certificate Menu -> Install a certificate for Mac.

\-> If the bug still happens, it seems there is a bug in the Automatic Setup feature, please [create a new ticket](https://github.com/ProxymanApp/Proxyman/issues) and let us know.

### 3. Proxyman could not record any traffic from my local server, e.g http://localhost:3000

By default, Traffic from http://localhost:3000 doesn't go through the system proxy. Therefore, Proxyman could not capture your traffic.&#x20;

Please follow this [solution](https://docs.proxyman.io/troubleshooting/couldnt-see-any-request-from-localhost-server) to fix it.

