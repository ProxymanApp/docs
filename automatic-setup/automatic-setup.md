---
description: >-
  Use Proxyman Automatic Setup to open a pre-configured Terminal and capture
  HTTP/HTTPS traffic from NodeJS, Python, Ruby, Golang and cURL in one click.
---

# Automatic Setup

## 1. Problems

Proxyman **could not capture** HTTP/HTTPS traffic from the following setup:

* **NodeJS**: Axios, got, superagent, fetch, and node-fetch
* **Python**: http, https, aiohttp, requests
* **Ruby**: http, net/http, net/https, faraday, httparty, and fastlane
* Golang: net/http, fasthttp, resty, gorequest, req, grequests
* ElectronJS
* cURL

It's a known issue: NodeJS, Python, Ruby, and cURL run from the Terminal app don't use the system HTTP proxy. So there is no traffic in Proxyman.

You have to read the technical documentation of each library and manually configure:

* The HTTP Proxy
* Trust for a self-signed certificate

\=> Time-consuming and error-prone ❌

## 2. Solution: Automatic Setup

### Benefit:

* ✅ **1-click to automatically set up HTTP Proxy & Certificate** on a variety of dev environments
* Capture HTTP(s) traffic from NodeJS, Python, Ruby, Golang, Terminal or Web Browser, etc.
* Safe. It works in your current session and doesn't affect your OS

### How to use:

1. Open Proxyman -> **Setup** menu -> **Automatic Setup…**
2. Click **Open New Terminal…**. You can pick Apple Terminal, iTerm2, or Ghostty from the menu next to it.
3. Accept the AppleScript permission prompt if needed
4. The new Terminal window opens -> Start your backend server or run your scripts => Proxyman automatically captures all traffic.
5. Done ✅

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.18.19@2x.jpg" alt="Proxyman Automatic Setup window with the Open New Terminal button and the Web Browsers section"><figcaption><p>Start the pre-configured Terminal app</p></figcaption></figure>

<figure><img src="../.gitbook/assets/CleanShot 2023-04-26 at 15.53.00@2x.jpg" alt="Terminal window showing the Proxyman Automatic Setup scripts message, ready to start a backend server"><figcaption><p>New Terminal app is launched</p></figcaption></figure>

### Notes:

* Automatic Setup can open Apple Terminal, iTerm2, or Ghostty. To use another Terminal app (for example Hyper), select **My own Terminal…** in the same menu or use the [Manual Setup](manual-setup.md).
* It's safe because it only runs in your current session. It doesn't change your system configuration.

#### ElectronJS

1. Open a new Terminal from Automatic Setup
2. Use this command line:

```
open ~/Applications/your_electron_app.app
```

You can also click **Select ElectronJS App…** in the Automatic Setup window. See [ElectronJS](../debug-devices/electronjs.md).

### Support Libraries:

Proxyman (with Automatic Setup) works out of the box with the following network libraries.

* NodeJS: [axios](https://www.npmjs.com/package/axios), [fetch](https://nodejs.org/dist/latest-v18.x/docs/api/globals.html#fetch) (v18+), [node-fetch](https://www.npmjs.com/package/node-fetch), [got](https://www.npmjs.com/package/got), [https](https://nodejs.org/api/https.html), and [superagent](https://www.npmjs.com/package/superagent)
* Ruby: [http](https://ruby-doc.org/stdlib-3.0.2/libdoc/net/http/rdoc/Net/HTTP.html), [net/http](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html), [net/https](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html), [httparty](https://github.com/jnunemaker/httparty), [faraday](https://github.com/lostisland/faraday), and fastlane
* Python: [requests](https://pypi.org/project/requests/), [aiohttp](https://docs.aiohttp.org/en/stable/), http.client, urllib3 and httpx
* Golang: net/http, fasthttp, resty, gorequest, req, grequests
* ElectronJS app
* cURL without --proxy flag

{% hint style="success" %}
It's completely **SAFE** since the change only affects your current Terminal session. It doesn't change your **bash\_profile** or **zshrc** file.
{% endhint %}

## 3. Advanced: How does it work?

When you click **Open New Terminal…**, Proxyman does the following:

1. Uses AppleScript to start the Terminal app.
2. Runs this command line in the new Terminal window:

```bash
set -a && source "$HOME/.proxyman/proxyman_env_automatic_setup.sh" && set +a
```

3. proxyman\_env\_automatic\_setup.sh is a bash script that sets the environment variables Proxyman needs.

For example:

* HTTP\_PROXY & HTTPS\_PROXY env
* PATH
* RUBYLIB
* PYTHONPATH
* NODE\_OPTIONS
* GLOBAL\_AGENT\_HTTP\_PROXY

**NodeJS**:

1. Proxyman prepends a new Node directory to the $PATH env.
2. Proxyman monkey-patches Node with the [global-agent](https://www.npmjs.com/package/global-agent) package, which adds HTTP proxy support to axios and fetch.

**Ruby**:

1. Overrides $RUBYLIB to point to the Proxyman app
2. Patches common libraries, such as http, net/http and net/https -> Sets the HTTP proxy and trusts the Proxyman self-signed certificate.

**Python**:

1. Overrides $PYTHONPATH to point to the Proxyman app
2. Patches common libraries, such as aiohttp, httplib, http.client -> Sets the HTTP proxy and trusts the Proxyman self-signed certificate.

**Go**:

1. Overrides HTTP\_PROXY & HTTPS\_PROXY env
2. Overrides some Go env to trust the self-signed certificate

## 4. Troubleshooting

See the [Troubleshooting](troubleshooting.md) page.

## Learn more

* [Capture HTTP/HTTPS Request from axios (NodeJS)](https://proxyman.com/posts/2023-05-14-Capture-HTTP-HTTPS-Request-From-Axios-NodeJS)
* [Capture HTTP/HTTPS Request from Ruby (net::http, or http gem) scripts](https://proxyman.com/posts/2023-05-09-Capture-HTTP-HTTPS-Request-Response-From-Ruby-Net-HTTP-library)
* [How to capture HTTPS traffic from Python requests or httpx library](https://proxyman.com/posts/2025-01-29-How-To-Capture-HTTPS-Traffic-From-Python-Requests-httpx)
