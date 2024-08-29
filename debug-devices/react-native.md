# React Native

## 1. React Native - iOS

If you're using React Native for the iOS app, you can simply follow the iOS Guidelines. There is no difference from the iOS native app.

{% content-ref url="ios-device.md" %}
[ios-device.md](ios-device.md)
{% endcontent-ref %}

{% content-ref url="ios-simulator.md" %}
[ios-simulator.md](ios-simulator.md)
{% endcontent-ref %}

## 2. React Native - Android

Basically, To capture HTTP/HTTPS traffic from React Native for Android apps, it's similar to the native Android app. Please follow Android Setup Guide:

* [Android Physical Device](android-device/)
* [Android Emulator](react-native.md#android-emulator)

{% hint style="warning" %}
Make sure you've followed all steps in the Guideline, especially the **5th step**, where you add the **res/xml/network\_security\_config.xml** and **AndroidManifest.xml**

Otherwise, Proxyman could not decrypt the SSL connection.
{% endhint %}

## 3. Troubleshooting - Android

### 3.1 Metro bundle errors

After setting the HTTP Proxy from your Android to Proxyman, you might encounter the following error because Metro Bundle could not connect to its local server.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-06 at 07.58.01.png" alt=""><figcaption><p>Metro bundle errors</p></figcaption></figure>

To fix it:

#### Android Emulator

1. Open Proxyman -> Certificate menu -> Install for Android -> Emulator -> Click on the "Revert the Proxy"
2. Open Android Emulator -> Setting App -> Network -> Wifi -> Find a way to change the proxy
3. Change the HTTP Proxy manually by using the **Proxyman IP & Port**. If you don't know what the IP & Port is, open the Certificate menu -> Install for Android -> Physical Device -> In the 2nd section. Find the Server IP & Port.
4. Before saving, enter the `localhost` in the bypass Proxy List ✅

![CleanShot 2023-04-05 at 22 28 12 2@2x](https://user-images.githubusercontent.com/5878421/230129476-4bd5d1a0-c3c5-4c73-bb79-81f14a071e63.jpg)

5. Done
6. `The Bridge Was shutdown` warning and the metro bundle errors are gone ✅

#### Android Physical Device

1. Open Android Physical Device -> Setting App -> Network -> Wifi -> Find a way to change the proxy
2. Change the HTTP Proxy manually by using the Proxyman IP & Port. If you don't know what the IP & Port is, open the Certificate menu -> Install for Android -> Physical Device -> In the 2nd section. Find the Server IP & Port.
3. Before saving, enter them `your IP` in the bypass Proxy List ✅&#x20;
4. Done



Read more at: [https://github.com/ProxymanApp/Proxyman/issues/1407#issuecomment-1497235102](https://github.com/ProxymanApp/Proxyman/issues/1407#issuecomment-1497235102)

