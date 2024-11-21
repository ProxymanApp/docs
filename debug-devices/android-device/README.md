---
description: >-
  How to set up Android Device or Emulator with Proxyman to capture HTTP/HTTPS
  Requests/Response
---

# Android Device & Emulator

In order to capture and decrypt HTTP/HTTPS request/response from your physical Android Devices or Android Emulators, please navigate to:

* **Certificate** **Menu** -> **Install Certificate on Android -> Device**
* **Certificate Menu -> Install Certificate on Android -> Emulator**

{% hint style="info" %}
Check out the [Mini Tutorial on how to set up Android devices & emulators](sample-android-project.md)
{% endhint %}

{% hint style="info" %}
For the **Android Emulator**, let's check out the [Automatic Script for Android Emulator](automatic-script-for-android-emulator.md#1-whats-it)
{% endhint %}

## 1. Android Setup Guide

If you want to capture & decrypt HTTP/HTTPS Traffic from your Physical or Emulator Android Device, please follow all steps in the setup guide:

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-26 at 09.50.35.png" alt="" width="563"><figcaption><p>Setup Guide for Android Devices</p></figcaption></figure>

1. Certificate Menu -> Install Certificate on Android -> **Device**
2. Install **Root Proxyman Certificate** on your machine: You can follow the [macOS Guide](../macos.md).
3. Get your Android Device or Emulator -> Open Setting app -> Wifi -> Select the current Wifi -> Config the HTTP Proxy by following the next tables.

| Name           | Value                                             |
| -------------- | ------------------------------------------------- |
| Server IP      | Your current IP Network                           |
| Port           | The current port of Proxyman: 9090 is the default |
| Authentication | No                                                |

{% hint style="info" %}
Some Samsung devices couldn't access the Internet after setting the HTTP Proxy. Please try to forget your current network and connect again.

If **you're using any VPN app**, please make sure to close it, since some VPN apps conflict with HTTP/HTTPS Proxy configs.
{% endhint %}

&#x20; 3\. Open [http://proxy.man/ssl](http://proxy.man/ssl) from the native web browser on your Android Devices in order to install the Proxyman Certificate.

### **Android 11, Android 12 or later:**

* Visit http://proxy.man/ssl from the Google Chrome app to download the certificate.
* From Android 11 or later, you have to manually install the certificate in the Setting app.
* Settings app -> Security -> Encryption & Credentials -> Install a Certificate -> Selec "CA Certificate" -> Select Proxyman CA Certificate in your storage.

### **Android 10 and below:**

* As soon as you visit http://proxy.man/ssl, your Android devices will download and install it automatically. Make sure you select the **VPN and App Section**.

{% hint style="info" %}
**On Android 12+**, If you encounter this warning "Can't install the Certificate: This file can't be used as a VPN & app user certificate", please try to select "CA Certificate" instead.&#x20;

Ref: [https://stackoverflow.com/a/70261393/3127477](https://stackoverflow.com/a/70261393/3127477)
{% endhint %}

{% hint style="info" %}
**http://proxy.man/ssl** is a local website, which serves from the local Proxyman's HTTP server. If you couldn't open it, please forget the wifi, re-connect and make sure the Proxyman app is opening.
{% endhint %}

4\. On Android 11 and Android 12. Let's verify by opening the Trusted Credentials -> User Tab.

Make sure you can see the **Proxyman CA** Certificate like the below screenshot.

![Verify that Proxyman CA Certificate is installed properly](<../../.gitbook/assets/Screen\_Shot\_2020-09-29\_at\_9\_00\_46\_PM (1).png>)

&#x20;   5\. Open your app Source Code: Adding the two following `xml` files.

* Add **res/xml/network\_security\_config.xml**

{% code title="network_security_config.xml" %}
```markup
<network-security-config>
  <debug-overrides>
    <trust-anchors>
      <!-- Trust user added CAs while debuggable only -->
      <certificates src="user" />
      <certificates src="system" />
    </trust-anchors>
  </debug-overrides>

  <base-config cleartextTrafficPermitted="true">
    <trust-anchors>
      <certificates src="system" />
      <certificates src="user" />
    </trust-anchors>
  </base-config>
</network-security-config>
```
{% endcode %}

* Add to **AndroidManifest.xml**

{% code title="manifest.xml" %}
```markup
<?xml version="1.0" encoding="utf-8"?>
<manifest ... >
    <application android:networkSecurityConfig="@xml/network_security_config" ... >
    ...
    </application>
</manifest>
```
{% endcode %}

{% hint style="info" %}
Find more information at [Network Security Configuration ](https://developer.android.com/training/articles/security-config.html)
{% endhint %}

{% hint style="info" %}
Make sure that you **remove those configs in the Release build**. If not, your HTTP/HTTPS requests can be intercepted and leak your sensitive data in the Production build.
{% endhint %}

6\. If it's Android Emulator, please restart the emulator

7\. Done ✅

## **2. Troubleshooting**

Please check out this [troubleshooting section.](sample-android-project.md#4-troubleshooting)

## 3. Sample Android Project

If you've struggled to config XML settings, let's check out this simple project that we've configured:

Github Link: [https://github.com/ProxymanApp/OKHTTP-Android-Sample](https://github.com/ProxymanApp/OKHTTP-Android-Sample)

{% content-ref url="sample-android-project.md" %}
[sample-android-project.md](sample-android-project.md)
{% endcontent-ref %}

## 4. React Native Android app

If you're using React Native for the Android app, please check out the [React Native Page](../react-native.md).

## 5. Intercept Traffic from embedding WebView

Some Android apps have embedded WebView that requires extra steps in order to intercept HTTPS traffic.

1. Make sure you're able to see other HTTPS traffic from your Android app. It means that you've set up the certificate properly
2. Inject the following code to your WebView

```java
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
    WebView.setWebContentsDebuggingEnabled(true);
}

// The following two lines help with disabling asset caching
webView.getSettings().setAppCacheEnabled(false);
webView.getSettings().setCacheMode(WebSettings.LOAD_NO_CACHE);
```

&#x20; 3\. Open a new Chrome tab on your computer and navigate to `chrome://inspect`

4\. When you open the WebView, the view will appear in your Chrome tab, then you can simply click  `inspect` to start using the remote debugger.

## 6. SSL Proxying using Root Device

> Credit for [Shirshak](https://github.com/shirshak55)

If your Android version is below 7 you don't need to do this step. Google added extra security that doesn't allow man-in-middle-app to attack after Android 6. i.e unable to do MITM attack on android apps.

We don't bear any responsibility for problems caused by rooting phones. So please follow the guide at your own risk.

1. Root your phone with `magisk` framework.
2. Install the Root file browser so you can copy and paste files in a restricted system folder.
3.  Type the following script in the command line

    ```bash
    $ cd ~/.proxyman
    // We copy certificate to another file name just so we may need it later
    $ cp proxyman-ca.pem temp.pem
    $ hash=$(openssl x509 -inform PEM -subject_hash_old -in temp.pem | head -1)
    $ mv temp.pem "$hash.0"
    ```
4. If you go to `~/.proxyman` folder you must notice a file name starting with numbers with extension
5. Copy that file to your Android.
6. Using root file browser transfer that file to /system/etc/security/cacerts/
7. Enjoy proxying.

{% hint style="info" %}
1. When using Android phones, set the gateway to any wrong IP just so you can be sure all your traffic goes from proxy man proxy only.
2. We can use the macOS sharing feature to create a mobile hotspot. And from an Android phone, you can use Proxyman proxy easily. It is much better because sometimes the router can block requests between mobile and macOS.
{% endhint %}

## Additional Resources

* Mitmproxy has a useful tutorial on how to install Proxyman Certificate on your Android Emulator: [https://docs.mitmproxy.org/stable/howto-install-system-trusted-ca-android/](https://docs.mitmproxy.org/stable/howto-install-system-trusted-ca-android/)
