---
description: >-
  Use Proxyman Manual Setup to capture HTTPS traffic from NodeJS, Python, Ruby
  and cURL in your own Terminal app, such as iTerm2, with Bash, Zsh or Fish.
---

# Manual Setup

## 1. Problems

Proxyman **could not capture** HTTP/HTTPS traffic from the following setup:

* **NodeJS**: Axios, got, superagent, fetch, and node-fetch
* Python: http, https, aiohttp, requests
* Ruby: http, net/http, net/https, faraday, httparty and fastlane
* cURL

It's a known issue: NodeJS, Python, Ruby, and cURL run from the Terminal app don't use the system HTTP proxy. So there is no traffic in Proxyman.

You have to read the technical documentation of each library and manually configure:

* The HTTP Proxy
* Trust for a self-signed certificate

\=> Time-consuming and error-prone ❌

## 2. Solution: Manual Setup

### Benefit:

* ✅ Run on your favorite Terminal app: iTerm2 with Bash, Zsh, and Fish Shell
* Capture HTTP(s) traffic from NodeJS, Python, Ruby, Terminal or Web Browser, etc.
* Safe. It works in your current session and doesn't affect your OS

### How to use:

1. Open Proxyman -> **Setup** menu -> **Manual Setup…**
2. Open your favorite Terminal app, such as iTerm2
3. Click **Copy to Clipboard**, then paste the command into your Terminal and run it
4. Done ✅
5. Start your backend server or run a script => Proxyman automatically captures all HTTP/HTTPS traffic

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.23.20@2x.jpg" alt="Proxyman Manual Setup window with the command to copy, next to iTerm running the pasted command"><figcaption><p>Manual Setup</p></figcaption></figure>

### Support Libraries:

Proxyman (with Manual Setup) works out of the box with the following network libraries.

* NodeJS: [axios](https://www.npmjs.com/package/axios), [fetch](https://nodejs.org/dist/latest-v18.x/docs/api/globals.html#fetch) (v18+), [node-fetch](https://www.npmjs.com/package/node-fetch), [got](https://www.npmjs.com/package/got), [https](https://nodejs.org/api/https.html), and [superagent](https://www.npmjs.com/package/superagent)
* Ruby: [http](https://ruby-doc.org/stdlib-3.0.2/libdoc/net/http/rdoc/Net/HTTP.html), [net/http](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html), [net/https](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html), [httparty](https://github.com/jnunemaker/httparty), [faraday](https://github.com/lostisland/faraday), and fastlane
* Python: [requests](https://pypi.org/project/requests/), [aiohttp](https://docs.aiohttp.org/en/stable/), http.client, urllib3 and httpx
* cURL without --proxy flag

## 3. Advanced: How does it work?

See [Automatic Setup: How does it work?](automatic-setup.md#3.-advanced-how-does-it-work)

## 4. Troubleshooting

See the [Troubleshooting](troubleshooting.md) page.
