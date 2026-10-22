---
description: >-
  Requests from axios, fetch, Alamofire, Ktor or cURL not showing in Proxyman?
  Use Automatic Setup, Network Extension, or set the HTTP proxy in the library.
---

# I couldn't see any requests from 3rd-party network libraries

## 1. Problem

* I can see other requests in Proxyman, but not the ones from my website, NodeJS, iOS, or Android app that use 3rd-party network libraries, such as [fetch](https://github.com/github/fetch), [axios](https://github.com/axios/axios), [Alamofire](https://github.com/Alamofire/Alamofire), [Ktor Apache HttpClient](https://ktor.io), curl, ...

{% hint style="info" %}
If a library running on your Mac ignores proxy settings, try [Network Extension](../advanced-features/network-extension.md). It captures supported HTTP/HTTPS traffic without changing the library's proxy settings. HTTPS still needs certificate trust and [SSL Proxying](../basic-features/ssl-proxying.md).

Network Extension is BETA and requires Proxyman PRO on macOS 26 or later.
{% endhint %}

## 2. New Automatic Solution (v4.7.0 or later) ✅

Proxyman v4.7.0 or later can capture HTTP/HTTPS traffic from NodeJS, Python and Ruby scripts with one click.

* One-click solution: no need to set the HTTP proxy or trust the self-signed certificate by hand.
* Supports NodeJS, Ruby and Python. Newer versions also support Golang.

### How to use

1. Open Proxyman -> **Setup** menu -> **Automatic Setup…**
2. Click **Open New Terminal…**
3. Accept the AppleScript permission prompt if needed.
4. A new Terminal window opens. Start your Python backend server or run your scripts there. Proxyman captures all their traffic.
5. Done ✅

<figure><img src="../.gitbook/assets/proxyman-automatic-setup-window.jpg" alt="Proxyman Automatic Setup window with Terminal App, Web Browsers and ElectronJS App sections"><figcaption><p>Open a pre-configured Terminal with Automatic Setup</p></figcaption></figure>

See [I could not see any HTTP traffic from my NodeJS, Python, or Ruby scripts](i-could-not-see-any-http-traffic-from-my-nodejs-python-or-ruby-scripts.md) for more details.

## 3. Old Solution (Not recommended ❌)

In general, you have to set up the network library to use an HTTP proxy that points to the Proxyman port (9090 by default).

List of possible solutions:

* Fetch: [Using a proxy like Fiddler with the Fetch API (Stack Overflow)](https://stackoverflow.com/questions/44524236/using-proxy-like-fiddler-with-fetch-api)
* cURL: Use the _--proxy_ flag. For example:

```
$ curl -v "https://httpbin.org/get?id=123" --proxy localhost:9090
```

Read more: [cURL with a proxy (Stack Overflow)](https://stackoverflow.com/a/9445516/3127477)

* Ktor: [Ktor client proxy documentation](https://ktor.io/docs/client-proxy.html)
* Alamofire: [Alamofire with a proxy (Stack Overflow)](https://stackoverflow.com/a/42754358/3127477)

### Axios

You can set the HTTP proxy in Axios. Then all its traffic appears in Proxyman.

```javascript
axios.get({
  url: '/v1/user/data',

  // 'proxy' defines the hostname and port of the proxy server
  // Use `false` to disable proxies, ignoring environment variables.
  // `auth` indicates that HTTP Basic auth should be used to connect to the proxy, and
  // supplies credentials.
  // This will set an `Proxy-Authorization` header, overwriting any existing
  // `Proxy-Authorization` custom headers you have set using `headers`.
  proxy: {
    host: '127.0.0.1',
    port: 9090
  }
});
```

Proxyman listens on port 9090 by default. To find your Mac's IP address and port, see the [iOS setup guide](../debug-devices/ios-device.md#ios-setup-guide).

## Learn more

* [Capture HTTP/HTTPS requests from Axios in NodeJS](https://proxyman.com/posts/2023-05-14-Capture-HTTP-HTTPS-Request-From-Axios-NodeJS)
