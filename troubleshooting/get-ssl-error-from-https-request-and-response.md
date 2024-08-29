# SSL Error from HTTPS Request/Response

## 1. Problems

* You could not see any HTTPS traffic on the Proxyman app
* You get SSL Error from HTTPS Requests and Responses.
* You get **SSL Handshake Failed**

![](<../.gitbook/assets/Screen Shot 2020-04-25 at 19.52.38.png>)

## 2. Solution

There are many reasons why SSL Handshake Failed, please walk through the below steps to address the problem.

## 2.1 Mobile devices

### iOS Device&#x20;

* Follow this [iOS Setup Guide](../debug-devices/ios-device.md) -> Make sure you've installed & trusted the Proxyman CA Certificate on your device.
* If you're intercepting some popular apps (e.g. Facebook, Instagram, Apple, Whatsapp, ...): They are protected by SSL Pinning -> Impossible to intercept them.
* Verify that your iOS app doesn't have SSL Pinning. If yes, please disable it.

### iOS Simulator

Follow this [iOS Simulator Setup Guide](../debug-devices/ios-simulator.md) -> Make sure you've installed & trusted the Proxyman CA Certificate on your device.

### Android Device

* Follow this [Android Device Setup Guide](../debug-devices/android-device/) -> Make sure you've installed & trusted the Proxyman CA Certificate on your device.
* Verify that the 5th step is completed (by adding your domain to two files: **res/xml/network\_security\_config.xml** and **AndroidManifest.xml**)
* If you're trying to intercept Android apps that you're not an owner -> It isn't possible to intercept -> ❌

### Android Emulator

* Follow this [Android Emulator Setup Guide](../debug-devices/android-device/automatic-script-for-android-emulator.md) -> Make sure you've installed & trusted the Proxyman CA Certificate on your device.
* Verify that the 5th step is completed (by adding your domain to two files: **res/xml/network\_security\_config.xml** and **AndroidManifest.xml**)
* If you're trying to intercept Android apps that you're not an owner -> It isn't possible to intercept -> ❌

### React Native app

* If your app is a React Native app, please follow the [React Native Guide](../debug-devices/react-native.md).

### Flutter

* Please follow [Flutter Setup Guide](../debug-devices/flutter.md)

If you've tried and verified all the above steps, but still get SSL Errors?

### Verify that you're able to see HTTPS Request/Response from https://google.com without any errors

1. Get your devices&#x20;
2. Open the Web Browser (Safari on iOS or Google Chrome on Android)
3. Visit **https://google.com**
4. Select "Enable SSL Proxying" on this domain on the Proxyman app for macOS
5. Verify if you're able to see the HTTPS Response or not.

#### ✅  Success

1. You're able to see https://google.com HTTPS Response, which means you set up the Certificate correctly -> It's good ✅
2. The problem might be from your apps. Let's try again on your domains/apps -> If the SSL Error still happens, a high chance that this app is protected by the SSL Pinning.
3. If you believe that it's not an SSL Pinning case, please open a ticket on [Github](https://github.com/ProxymanApp/Proxyman/issues) (Please mention what device, OS Version, app name, etc)

#### ❌ Failed!

* It seems Proxyman Certificate is not installed or trusted correctly in your devices. Please go back to the [2.1 Mobile Device](get-ssl-error-from-https-request-and-response.md#2.1-mobile-devices) section and follow it.
* If you verify that everything is done, but the SSL Error still happens, please open a ticket on [Github](https://github.com/ProxymanApp/Proxyman/issues) (Please mention what device, OS Version, app name, etc)

## 2.2 Macbook or Windows PC

I get SSL Errors from:

* **Mac devices (Macbook, Mac Mini, Mac Studio)** -> Install & Trust the Certificate on your Macbook -> Follow [macOS Guide](../debug-devices/macos.md)
* **Windows** -> Install and trust the certificate on your Windows machine  -> Follow [Windows guide](broken-reference)&#x20;
* Java -> Follow [Java VM Guide](../debug-devices/java.md)
* Firefox -> Follow [Firefox Guide](../debug-devices/firefox.md)
* Python -> Follow [Python Guide](../debug-devices/python.md)
* Ruby -> Follow [Ruby Guide](../debug-devices/ruby.md)

{% hint style="warning" %}
Some networking libraries (Ruby, NodeJS, Python, Golang) don't trust the self-signed certificate by default. We have to explicitly tell the library to trust the certificate.

\=> To fix it, please google **"\<Your framework/library> self-signed certificate",** a found some answers on StackOverflow.
{% endhint %}

## 2.3 SSL-Pinning?

* You're still unable to see HTTPS Response on your app, it seems that your app is protected by [SSL-Pinning](https://en.wikipedia.org/wiki/HTTP\_Public\_Key\_Pinning), which prevents MitM apps from seeing the content. All popular apps (Facebook, Apple, Instagram, Messenger, etc.) have this feature.
* Please temporarily **disable SSL-Pinning** and try again.

Read more about SSL-Pining: [https://www.raywenderlich.com/1484288-preventing-man-in-the-middle-attacks-in-ios-with-ssl-pinning](https://www.raywenderlich.com/1484288-preventing-man-in-the-middle-attacks-in-ios-with-ssl-pinning)&#x20;



{% hint style="info" %}
If you've tried everything but are not sure what is wrong? Please open a [Github ticket](https://app.gitbook.com/o/-LlPtWiscJCRFiRPxWvB/s/-LlPt\_6BePnJ3oK3saP1/).

Please also mention: Proxyman macOS/Windows, Proxyman version, your iOS/Android device, etc.
{% endhint %}
