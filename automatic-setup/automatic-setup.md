---
description: 1-click to capture HTTP/HTPS traffic from NodeJS, Ruby and Python
---

# Automatic Setup

## 1. Problems

Proxyman **could not capture** HTTP/HTTPS traffic from the following setup:

* **NodeJS**: Axios, got, superagent, fetch, and node-fetch
* **Python**: http, https, aiohttp, requests
* **Ruby**: http, net/http, net/htps, faraday, and httparty, fastlane
* Golang: net/http, fasthttp, resty, gorequest, req, grequests
* ElectronJS
* cURL

It's a known issue since NodeJS, Python, Ruby, and cURL which are executed from the Terminal app, don't respect the system HTTP Proxy. Thus, there is no traffic on Proxyman.

You have to read through the Technical Documentation of each library and manually config:

* The HTTP Proxy
* Trust a self-signed certificate

\=> Time-consuming and error-prone ❌

## 2. Solution: Automatic Setup

### Benefit:

* ✅ **1-click to automatically set up HTTP Proxy & Certificate** on a variety of dev environments
* Capture HTTP(s) traffic from NodeJS, Python, Ruby, Terminal or Web Browser, etc
* Safe. Work on your current session, not affect your OS

### How to use:

1. Open Proxyman -> Setup Menu -> Automatic Setup
2. Click on "Open New Terminal"
3. Accept the Apple Script permission prompt if needed
4. The New Terminal app is launched -> You can start your Backend Server, or Run scripts => Proxyman automatically captures all traffic.
5. Done ✅

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.18.19@2x (1).jpg" alt=""><figcaption><p>Start the pre-configured Terminal app</p></figcaption></figure>

<figure><img src="../.gitbook/assets/CleanShot 2023-04-26 at 15.53.00@2x.jpg" alt=""><figcaption><p>New Terminal app is launched</p></figcaption></figure>

### Notes:

* Only the pre-configured Terminal app is able to capture HTTP traffic out of the box. If you would like to use your own Terminal app (e.g. iTerm2, Hyper, etc), please use the Manual Setup.
* It's totally safe because it runs on your current session. It doesn't alter your System Config.

#### ElectronJS

1. Open the Automatic Terminal
2. Use this command line:

```
open ~/Applications/your_electron_app.app
```

### Support Libraries:

Proxyman (with Automatic Setup) can work out of the box with the following network libraries.

* NodeJS: [axios](https://www.npmjs.com/package/axios), [fetch](https://nodejs.org/dist/latest-v18.x/docs/api/globals.html#fetch) (v18+), [node-fetch](https://www.npmjs.com/package/node-fetch), [got](https://www.npmjs.com/package/got), [https](https://nodejs.org/api/https.html), and [superagent](https://www.npmjs.com/package/superagent)
* Ruby: [http](https://ruby-doc.org/stdlib-3.0.2/libdoc/net/http/rdoc/Net/HTTP.html), [net/http](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html), [net/https](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html), [httparty](https://github.com/jnunemaker/httparty), and [faraday](https://github.com/lostisland/faraday), fastlane
* Python: [request](https://pypi.org/project/requests/), [aiohttp](https://docs.aiohttp.org/en/stable/), http.client, urllib3 and httpx
* Golang: net/http, fasthttp, resty, gorequest, req, grequests
* ElectronJS app
* cURL without --proxy flag

{% hint style="success" %}
It's completely **SAFE** since the change only affects your current Terminal Session. It doesn't alter your **bash\_profile** or **zshrc** file.
{% endhint %}

## 3. Advanced: How does it work?

As soon as you click on the "Open New Terminal" button, Proxyman would perform a series of automatic actions:

1. Use AppleScript to start the Terminal app.
2. With the new Terminal app, it starts running this command line:&#x20;

```bash
set -a && source "$HOME/.proxyman/proxyman_env_automatic_setup.sh" && set +a
```

3. proxyman\_env\_automatic\_setup.sh is a bash script that defines new Variable Environments that helps Proxyman.

For example:

* HTTP\_PROXY & HTTPS\_PROXY env
* PATH
* RUBYLIB
* PYTHONPATH
* NODE\_OPTIONS
* GLOBAL\_AGENT\_HTTP\_PROXY

**NodeJS**:

1. Proxyman prepends a new Node directory into the $PATH env.
2. Monkey-patching the node with a [global-agent ](https://www.npmjs.com/package/global-agent)package, which supports HTTP Proxy for axios, and fetch out of the box

**Ruby**:

1. Override the $RUBYLIB to Proxyman app
2. Patching all common libraries, such as http, net/http and net/https, etc -> Set HTTP Proxy and trust Proxyman self-signed certificate.

**Python**:

1. Override $PYTHONPATH to Proxyman app
2. Patching all common library, such as aiohttp, httplib, http.client -> Set HTTP Proxy and trust Proxyman self-signed certificate.&#x20;

## 4. Troubleshooting

See the [Troubleshooting](troubleshooting.md) page
