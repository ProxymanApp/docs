---
description: Capture HTTP/HTTPS Traffic from Ruby with Proxyman
---

# Ruby

## 1. New Automatic Solution (v4.7.0 or later) ✅

Proxyman v4.7.0 or later can capture HTTP/HTTPS traffic from Ruby with 1-click.

* 1-click solution: No need to manually set HTTP Proxy config or trust the self-signed certificate.
* Support many Ruby libraries: http, net/http, net/https, httparty, and faraday.

### How to use:

1. Open Proxyman -> Setup Menu -> Automatic Setup
2. Click on "Open New Terminal"
3. Accept the Apple Script permission prompt if needed
4. The New Terminal app is launched -> You can start your Ruby Backend Server, or Run scripts => Proxyman automatically captures all traffic.
5. Done ✅

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.18.19@2x.jpg" alt=""><figcaption><p>Capture Traffic from Ruby</p></figcaption></figure>

## 2. Old Solution (Not Recommended)

### 1. Set HTTP Proxy to Ruby

Net::HTTP will automatically create a proxy from the `http_proxy` environment variable if it is present.&#x20;

So you can use:

```bash
ENV['http_proxy'] = 'http://127.0.0.1:9090' # your http://address:port here
```

and Net::HTTP will use it for all requests by default.

Ref: [https://stackoverflow.com/questions/15792999/how-to-set-a-proxy-in-rubys-net-http](https://stackoverflow.com/questions/15792999/how-to-set-a-proxy-in-rubys-net-http)

### 2. Install Proxyman Certificate on Ruby

By default, **Ruby** on macOS might not trust Proxyman's self-signed certificate. As a result, you might encounter SSL Error if you try to intercept HTTPS traffic.

You can explicitly tell Ruby to use Proxyman Certificate by using `SSL_CERT_FILE` env.

```bash
$ env SSL_CERT_FILE=~/.proxyman/proxyman-ca.pem ruby my_script.rb
```
