# I couldn't see any requests from 3rd-party network libraries

###

## 1. Problem

* I can see other requests on Proxyman but not from my website, NodeJS, iOS, or Android, .... which use 3rd-party network libraries, such as [fetch](https://github.com/github/fetch), [axios](https://github.com/axios/axios), [Alamofire](https://github.com/Alamofire/Alamofire), [Ktor Apache HttpClient](https://ktor.io), curl...

## 2. New Automatic Solution (v4.7.0 or later) ✅

Proxyman v4.7.0 or later can capture HTTP/HTTPS traffic from Python with 1-click.

* 1-click solution: No need to manually set HTTP Proxy config or trust the self-signed certificate.
* Support NodeJS, Ruby and Python.

### How to use:

1. Open Proxyman -> Setup Menu -> Automatic Setup
2. Click on "Open New Terminal"
3. Accept the Apple Script permission prompt if needed
4. The New Terminal app is launched -> You can start your Python Backend Server, or Run scripts => Proxyman automatically captures all traffic.
5. Done ✅

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.18.19@2x.jpg" alt=""><figcaption></figcaption></figure>

## 3. Old Solution (Not recommended ❌)

In general, we have to manually config the network library to use HTTP Proxy and point to Proxyman Port (Default at 9090)

List of possible solutions:

* Fetch: [https://stackoverflow.com/questions/44524236/using-proxy-like-fiddler-with-fetch-api](https://stackoverflow.com/questions/44524236/using-proxy-like-fiddler-with-fetch-api)
* cURL: Use _--proxy_ flag. For example:

```
$ curl -v "https://httpbin.org/get?id=123" --proxy localhost:9090
```

Read more: [https://stackoverflow.com/a/9445516/3127477](https://stackoverflow.com/a/9445516/3127477)

* Ktor: [https://ktor.io/clients/http-client/features/proxy.html](https://ktor.io/clients/http-client/features/proxy.html)
* Alamofire: [https://stackoverflow.com/a/42754358/3127477](https://stackoverflow.com/a/42754358/3127477)

#### Axios

You can explicitly set HTTP Proxy on Axios. All traffic will appear on Proxyman.

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

For the host and port value, you can find it in [iOS Device Windows](../debug-devices/ios-device.md#ios-setup-guide)
