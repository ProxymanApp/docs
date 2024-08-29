# Flutter

Currently, [Flutter does not use the system-level proxy](https://github.com/flutter/flutter/issues/20376), so if you use Proxyman, you might not see any traffic from your Flutter Project.

The good news is that you can work around this issue by manually configuring Flutter’s HTTP client to use Proxyman as its proxy.&#x20;

In general, we have to manually config the HTTP Client to proxy all traffic to Proxyman Proxy Server, which is listening at IP = localhost, port = 9090.

### How to use Proxyman & Flutter

1. Open Proxyman -> Certificate Menu -> Install Certificate on Android -> Physical Device.
2. Make sure you follow all steps, **except** step 2: Config Wifi Proxy

![](<../.gitbook/assets/Screen Shot 2021-09-14 at 10.52.27.png>)



For step 2:

Depending on which HTTP client you’re using, the steps will be slightly different. We will cover some popular HTTP Clients:

* Dart’s [HttpClient](https://api.dartlang.org/stable/2.4.1/dart-io/HttpClient-class.html) class
* The [http](https://pub.dev/packages/http) package
* [Dio](https://pub.dev/packages/dio)

If you're using Android Emulator, you can use `String proxy = 'localhost:9090'`. Otherwise, please use `String proxy = '<YOUR_LOCAL_IP>:9090'` on Android Physical Devices.

#### Dart HTTPClient Class

```java
// Make sure to replace <YOUR_LOCAL_IP> with 
// the external IP of your computer if you're using Android. 
// You can get the IP in the Android Setup Guide window
String proxy = Platform.isAndroid ? '<YOUR_LOCAL_IP>:9090' : 'localhost:9090';

// Create a new HttpClient instance.
HttpClient httpClient = new HttpClient();

// Hook into the findProxy callback to set
// the client's proxy.
httpClient.findProxy = (uri) {
  return "PROXY $proxy;";
};

// This is a workaround to allow Proxyman to receive
// SSL payloads when your app is running on Android
httpClient.badCertificateCallback = 
  ((X509Certificate cert, String host, int port) => Platform.isAndroid);
```

#### HTTP Package

```java
// Make sure to replace <YOUR_LOCAL_IP> with 
// the external IP of your computer if you're using Android. 
// You can get the IP in the Android Setup Guide window
String proxy = Platform.isAndroid ? '<YOUR_LOCAL_IP>:9090' : 'localhost:9090';

// Create a new HttpClient instance.
HttpClient httpClient = new HttpClient();

// Hook into the findProxy callback to set
// the client's proxy.
httpClient.findProxy = (uri) {
  return "PROXY $proxy;";
};

// This is a workaround to allow Proxyman to receive
// SSL payloads when your app is running on Android.
httpClient.badCertificateCallback = 
  ((X509Certificate cert, String host, int port) => Platform.isAndroid);

// Pass your newly instantiated HttpClient to http.IOClient.
IOClient myClient = IOClient(httpClient);

// Make your request as normal.
var response = myClient.get('/my-url');
```

#### Dio

```java
// Make sure to replace <YOUR_LOCAL_IP> with 
// the external IP of your computer if you're using Android. 
// You can get the IP in the Android Setup Guide window
String proxy = Platform.isAndroid ? '<YOUR_LOCAL_IP>:9090' : 'localhost:9090';

// Create a new Dio instance.
Dio dio = Dio();

// Tap into the onHttpClientCreate callback
// to configure the proxy just as we did earlier.
(dio.httpClientAdapter as DefaultHttpClientAdapter).onHttpClientCreate = (client) { 
  // Hook into the findProxy callback to set the client's proxy.
  client.findProxy = (url) {
    return 'PROXY $proxy'?;
  };
  
  // This is a workaround to allow Proxyman to receive
  // SSL payloads when your app is running on Android.
  client.badCertificateCallback = (X509Certificate cert, String host, int port) => Platform.isAndroid;
}
```

#### 3. Continue following the Step 3, 4, and 5 to capture SSL Traffic

At this point, you can see HTTP/HTTPS Traffic on Proxyman. However, in order to intercept HTTPS Traffic, you must follow the Step 3, 4, and 5 on the Android Setup Guide.

If you haven't done it yet, you might encounter SSL Errors.

#### Credit & Reference

Credit to James Dixon from [https://flutterigniter.com/debugging-network-requests/](https://flutterigniter.com/debugging-network-requests/)

