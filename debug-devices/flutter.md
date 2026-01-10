---
description: >-
  How to use Proxyman to capture HTTPS traffic. Works with iOS and Android
  Devices and Simulators
---

# Flutter

## ✅ 1. New Solution

{% hint style="success" %}
From Proxyman 6.4.0 or later, or Windows/Linux 3.7.0 or later
{% endhint %}

### Android Emulators

Proxyman can capture HTTPS from your Flutter app on the Android Emulator in 1 click. No need to modify your Flutter code, like the old solution.

1. Start Proxyman -> Certificate Menu -> Install Certificate for Android -> Emulators
2. Make sure set up your Android Emulator first, and the Android must is Google APIs.

Refer [automatic-script-for-android-emulator.md](android-device/automatic-script-for-android-emulator.md "mention")to understand how to set up your Android Emulators

3. Check "Install Proxyman VAN to Android Emulators"
4. Click "Override All Emulators"

<figure><img src="../.gitbook/assets/Screenshot 2026-01-10 at 19.29.46.jpg" alt="capture https from Flutter app Android Emulator with Proxyman"><figcaption><p>Capture https from Flutter app Android Emulator with Proxyman</p></figcaption></figure>

5. New Terminal will open and execute our bash script to override your Emulators.
6. When it's done, a New VPN App is installed to your Emulators
7. Click to the VPN button to start it -> Done ✅
8. Try to open your Flutter app, and make HTTPS Requests, Proxyman will capture it ✅

<figure><img src="../.gitbook/assets/Screenshot 2026-01-10 at 19.43.10.jpg" alt="Local VPN, routes all traffic to Proxyman app. Works with Flutter, React Native apps" width="563"><figcaption></figcaption></figure>

## ⚠️ 2. Old Solution

{% hint style="warning" %}
Old solution works with Proxyman macOS 6.3.0 and earlier, Windows/Linux 3.6.0 and earlier
{% endhint %}

### 2.1 Problem

[Flutter does not use the system-level proxy](https://github.com/flutter/flutter/issues/20376), so if you use Proxyman, you might not see any traffic from your Flutter Project.

The good news is that you can work around this issue by manually configuring Flutter’s HTTP client to use Proxyman as its proxy.

In general, we have to manually configure the HTTP Client to proxy all traffic to Proxyman Proxy Server, which is listening at IP = localhost, port = 9090.

#### 1. Set up Flutter (Required for all platforms - iOS & Android)

Depending on which HTTP client you’re using, the steps will be slightly different. We will cover some popular HTTP Clients:

* Dart’s [HttpClient](https://api.dartlang.org/stable/2.4.1/dart-io/HttpClient-class.html) class
* The [http](https://pub.dev/packages/http) package
* [Dio](https://pub.dev/packages/dio)

If you're using an Android Emulator or an iOS Simulator, you can use `String proxy = 'localhost:9090'`. Otherwise, please use `String proxy = '<YOUR_LOCAL_IP>:9090'` on Android Physical Devices.

You can find the \<YOUR\_LOCAL\_IP> from the Proxyman -> Certificate menu -> Install for iOS -> Physical Device

<figure><img src="../.gitbook/assets/1 (1).jpg" alt=""><figcaption><p>Use current IP</p></figcaption></figure>

Depending on the network library that your Flutter is using, please follow the settings below:

#### Dart HTTPClient Class

```dart
// Make sure to replace <YOUR_LOCAL_IP> with 
// the external IP of your computer if you're using Android. 
// You can get the IP in the Android Setup Guide window
String proxy = Platform.isAndroid ? '<YOUR_LOCAL_IP>:9090' : 'localhost:9090';

// Create a new HttpClient instance.
HttpClient httpClient = HttpClient();

// Hook into the findProxy callback to set
// the client's proxy.
httpClient.findProxy = (uri) {
  return "PROXY $proxy;";
};

// This is a workaround to allow Proxyman to receive
// SSL payloads when your app is running on Android
httpClient.badCertificateCallback = (cert, host, port) => true;
```

#### HTTP Package

```dart
// Make sure to replace <YOUR_LOCAL_IP> with 
// the external IP of your computer if you're using Android. 
// You can get the IP in the Android Setup Guide window
String proxy = Platform.isAndroid ? '<YOUR_LOCAL_IP>:9090' : 'localhost:9090';

// Create a new HttpClient instance.
HttpClient httpClient = HttpClient();

// Hook into the findProxy callback to set
// the client's proxy.
httpClient.findProxy = (uri) {
  return "PROXY $proxy;";
};

// This is a workaround to allow Proxyman to receive
// SSL payloads when your app is running on Android.
httpClient.badCertificateCallback = (cert, host, port) => true;

// Pass your newly instantiated HttpClient to http.IOClient.
IOClient myClient = IOClient(httpClient);

// Make your request as normal.
final response = myClient.get('/my-url');
```

### Dio ≥ v5.0.0 (Recommended)

```dart
// Make sure to replace <YOUR_LOCAL_IP> with 
// the external IP of your computer if you're using Android. 
// You can get the IP in the Android Setup Guide window
String proxy = Platform.isAndroid ? '<YOUR_LOCAL_IP>:9090' : 'localhost:9090';

// Create a new Dio instance.
Dio dio = Dio();

dio.httpClientAdapter = IOHttpClientAdapter(
  createHttpClient: () {
    final client = HttpClient();
    client.findProxy = (uri) {
      return 'PROXY $proxy';
    }
    client.badCertificateCallback = (cert, host, port) => true;
    return client;
  },
  validateCertificate: (cert, host, port) {
    return true;
  },
); 
```

#### Dio ＜ v5.0.0 (Deprecated APIs)

```dart
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
  client.badCertificateCallback = (X509Certificate cert, String host, int port) => true;
}
```

### 2. Flutter with iOS Simulators

1. Start your iOS Simulator from Flutter
2. On Proxyman -> Certificate menu -> Install Certificate for iOS -> Simulators
3. Follow all steps below

<figure><img src="../.gitbook/assets/2 (1).jpg" alt=""><figcaption><p>Install &#x26; trust Proxyman certificate to your iOS Simulators</p></figcaption></figure>

4. ✅ Done. Proxyman can capture your HTTPS.

### 3. Flutter with iOS Devices

* Follow this [Setup Guide](ios-device.md)

### 4. Flutter with Android Emulator

* Follow this [Setup Guide](android-device/automatic-script-for-android-emulator.md)

### 5. Flutter with Android Devices

* Follow this [Setup Guide](android-device/)

#### Credit & Reference

Credit to James Dixon from [https://flutterigniter.com/debugging-network-requests/](https://flutterigniter.com/debugging-network-requests/)
