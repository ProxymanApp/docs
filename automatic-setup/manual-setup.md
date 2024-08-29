# Manual Setup

## 1. Problems

Proxyman **could not capture** HTTP/HTTPS traffic from the following setup:

* **NodeJS**: Axios, got, superagent, fetch, and node-fetch
* Python: http, https, aiohttp, requests
* Ruby: http, net/http, net/htps, faraday, httparty and fastlane
* cURL

It's a known issue since NodeJS, Python, Ruby, and cURL which are executed from the Terminal app, don't respect the system HTTP Proxy. Thus, there is no traffic on Proxyman.

You have to read through the Technical Documentation of each library and manually config:

* The HTTP Proxy
* Trust a self-signed certificate

\=> Time-consuming and error-prone ❌

## 2. Solution: Manual Setup

### Benefit:

* ✅ Run on your favorite Terminal app: iTerm2 with Bash, Zsh, and Fish Shell
* Capture HTTP(s) traffic from NodeJS, Python, Ruby, Terminal or Web Browser, etc
* Safe. Work on your current session, not affect your OS

### How to use:

1. Open Proxyman -> Setup Menu -> Manual Setup
2. Open your favorite Terminal app, such as iTerm2
3. Copy & Paste the script to your Terminal -> Run it
4. Done ✅
5. You can start your Backend Server or run a script => Proxyman automatically captures all HTTP/HTTPS traffic out of the box

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.23.20@2x.jpg" alt=""><figcaption><p>Manual Setup</p></figcaption></figure>

### Support Libraries:

Proxyman (with Manual Setup) can work out of the box with the following network libraries.

* NodeJS: [axios](https://www.npmjs.com/package/axios), [fetch](https://nodejs.org/dist/latest-v18.x/docs/api/globals.html#fetch) (v18+), [node-fetch](https://www.npmjs.com/package/node-fetch), [got](https://www.npmjs.com/package/got), [https](https://nodejs.org/api/https.html), and [superagent](https://www.npmjs.com/package/superagent)
* Ruby: [http](https://ruby-doc.org/stdlib-3.0.2/libdoc/net/http/rdoc/Net/HTTP.html), [net/http](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html), [net/https](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html), [httparty](https://github.com/jnunemaker/httparty), [faraday](https://github.com/lostisland/faraday), and fastlane
* Python: [request](https://pypi.org/project/requests/), [aiohttp](https://docs.aiohttp.org/en/stable/), http.client, urllib3 and httpx
* cURL without --proxy flag

## 3. Advanced: How does it work?

See the [Automatic Setup: How does it work?](automatic-setup.md#3.-advanced-how-does-it-work)

## 4. Troubleshooting

See the [Troubleshooting](troubleshooting.md) page
