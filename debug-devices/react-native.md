---
description: >-
  Capture HTTPS traffic from React Native and Expo apps with Proxyman on iOS
  devices, iOS Simulators, Android devices and Android Emulators.
---

# React Native

## Video

{% embed url="https://www.youtube.com/watch?v=4LkKXyIPulM" %}
Capture HTTPS from a React Native Expo app on the iOS Simulator and Android Emulator
{% endembed %}

## 1. React Native - iOS

* If you're using React Native for the iOS app, follow the iOS guides. There is no difference from a native iOS app.
* Works with Expo or the Metro bundler

{% content-ref url="ios-device.md" %}
[ios-device.md](ios-device.md)
{% endcontent-ref %}

{% content-ref url="ios-simulator.md" %}
[ios-simulator.md](ios-simulator.md)
{% endcontent-ref %}

## 2. React Native - Android

Capturing HTTP/HTTPS traffic from React Native Android apps works like a native Android app. Please follow the Android setup guide:

* [Android Physical Device](android-device/)
* [Android Emulator](android-device/automatic-script-for-android-emulator.md)

{% hint style="warning" %}
Make sure you've followed all steps in the guide, especially the **5th step**, where you add the **res/xml/network\_security\_config.xml** and **AndroidManifest.xml**

Otherwise, Proxyman cannot decrypt the SSL connection.
{% endhint %}

## 3. Troubleshooting - Android

### 3.1 Metro bundle errors

After you set the HTTP Proxy on your Android device to Proxyman, you might get the following error, because the Metro bundler cannot connect to its local server.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-06 at 07.58.01.png" alt="React Native red screen on Android: Unable to load script, make sure you're running Metro"><figcaption><p>Metro bundle errors</p></figcaption></figure>

To fix it:

#### Android Emulator

1. Open Proxyman -> Certificate menu -> Install Certificate on Android -> Emulators… -> Click "Revert All Changes"
2. Open the Android Emulator -> Settings app -> Network -> Wi-Fi -> Open the proxy settings
3. Set the HTTP Proxy manually with the **Proxyman IP & Port**. If you don't know the IP & Port, open the Certificate menu -> Install Certificate on Android -> Physical Devices… and find the Server IP & Port in step 2.
4. Before saving, enter `localhost` in the bypass proxy list ✅

![Android Wi-Fi proxy settings with the Proxyman IP and port and localhost in the bypass proxy list](https://user-images.githubusercontent.com/5878421/230129476-4bd5d1a0-c3c5-4c73-bb79-81f14a071e63.jpg)

5. Done
6. The `The Bridge Was shutdown` warning and the Metro bundle errors are gone ✅

#### Android Physical Device

1. Open the Android physical device -> Settings app -> Network -> Wi-Fi -> Open the proxy settings
2. Set the HTTP Proxy manually with the Proxyman IP & Port. If you don't know the IP & Port, open the Certificate menu -> Install Certificate on Android -> Physical Devices… and find the Server IP & Port in step 2.
3. Before saving, enter `your IP` in the bypass proxy list ✅&#x20;
4. Done



Read more at: [https://github.com/ProxymanApp/Proxyman/issues/1407#issuecomment-1497235102](https://github.com/ProxymanApp/Proxyman/issues/1407#issuecomment-1497235102)

## Learn more

* [How to capture HTTP/HTTPS traffic from Expo React Native iOS and Android apps](https://proxyman.com/posts/how-to-capture-https-from-React-native-app-2025-update)
* [Capture HTTPS traffic from React Native apps with Proxyman](https://proxyman.com/posts/2023-09-25-Capture-HTTPs-Requests-From-React-Native-Apps)
* [Capture HTTP/HTTPS traffic from React Native apps with Proxyman](https://proxyman.com/react-native) (Proxyman website)
