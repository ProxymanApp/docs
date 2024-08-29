# Sample Android Project

## 1. What's it?

Intercepting HTTPS traffic on Android Devices and Android Emulators is more complicated than on iOS.&#x20;

If you've struggled to config XML settings, let's check out this sample project that we've already configured for you:

{% hint style="info" %}
Check out the [Sample Config section](sample-android-project.md#3-sample-config) to understand how the config is set up.
{% endhint %}

![Android OKHTTP + Proxyman](../../.gitbook/assets/Proxyman\_Android.png)

## 2. Prepare

* Android Studio
* Pixel 5 Emulator with **API 31+** (We suggest that we should create a brand-new Emulator device rather than using the current one. Visit Android Virtual Devices windows in Android Studio)
* Clone or download the project at [https://github.com/ProxymanApp/OKHTTP-Android-Sample](https://github.com/ProxymanApp/OKHTTP-Android-Sample)

{% hint style="warning" %}
"Small and Medium Phone" Android Emulator doesn't allow Proxyman or other MitM apps to decrypt HTTPS traffic.&#x20;

✅ We suggest using Pixel Emulator (Google APIs version).
{% endhint %}

## 3. Configuration

You might either follow steps 3.1 or 3.2:

### 3.1 Android Emulator with the Automatic Script

If you run this project on **Android Emulator (Google APIs version)**, you can check out the Automatic Script and Proxyman provides to:

1. Clone or download the project: [https://github.com/ProxymanApp/OKHTTP-Android-Sample](https://github.com/ProxymanApp/OKHTTP-Android-Sample)
2. Make sure you can run the project in Android Studio with Android Emulator (API 31)
3. Open Proxyman -> Certificate Menu -> Install Certificate for Android -> Emulator
4. Click on the "Override Emulator" button to automatically set the HTTP Proxy & Install & Trust the certificate.
5. You don't need to config the file  **res/xml/network\_security\_config.xml** and **AndroidManifest.xml** since the project is already configured.
6. Back to the Emulator -> Click on Say Hello -> Observe the HTTPS log on Proxyman
7. Done

### **3.2 Physical Android Devices**&#x20;

For Physical Devices or Emulator (without using the automatic script), it's more complicated and error-prone. Please carefully follow each following steps:

#### 3.2.1 Set HTTP Proxy to Proxyman

1. Open your Android Device -> Setting app -> Wifi: Make sure your Wifi connection is good. Sometimes, it's "Limited Connection" that you could not set the Wifi Proxy. If it happens, please remove the emulator and create a new one again.
2. Click on the Wifi then clicking on Edit Button.
3. Start set HTTP Proxy that the same IP and Port value from [Android Guideline](./) (Proxyman app -> Certificate -> Install Certificate on Android Devices)

{% hint style="info" %}
Make sure the Proxy Hostname and Port match with the values in (Proxyman app -> Certificate -> Install Certificate on Android Devices)
{% endhint %}

#### 2.3 Download and Install Proxyman Certificate

1. Open Google Chrome on your Android devices
2. Visit [http://proxy.man/ssl](http://proxy.man/ssl)
3. Download the Certificate and select VPN and App Category

{% hint style="info" %}
**On Android 12+**, If you encounter this warning "Can't install the Certificate: This file can't be used as a VPN & app user certificate", please try to select "CA Certificate" instead.&#x20;

Ref: [https://stackoverflow.com/a/70261393/3127477](https://stackoverflow.com/a/70261393/3127477)
{% endhint %}

4\. On Android 11 and Android 12. Let's verify by opening Trusted Credentials -> User Tab.

Make sure you can see Proxyman CA Certificate like the below screenshot.

![](<../../.gitbook/assets/Screen\_Shot\_2020-09-29\_at\_9\_00\_46\_PM (3).png>)

####

5\. You don't need to config the file  **res/xml/network\_security\_config.xml** and **AndroidManifest.xml** since the project is already configured.

6\. Back to the Emulator -> Click on Say Hello -> Observe the HTTPS log on Proxyman

7\. Done

## 4. Sample Config&#x20;

* **AndroidManifest.xml**

```markup
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="io.approov.shapes">

    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher"
        android:supportsRtl="true"
        android:theme="@style/AppTheme"
        android:name="io.approov.shapes.ShapesApp"
        android:networkSecurityConfig="@xml/network_security_config"
    >
        <activity android:name=".MainActivity" android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

* **res/xml/network\_security\_config.xml**

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

### 4. Troubleshooting

Depending on the Android Emulator and API version, you might encounter some errors.

**1.After setting the Wifi Proxy in Android Studio, I could not visit http://proxy.man/ssl**

\=> Please try to restart the Emulator and make sure the Wifi Status in Emulator is "**Connected"**

\=> Delete your Android Emulator and create a new one

**2. I get SSL Errors when intercepting HTTPS traffic**

\=> Sometimes, your Android Emulator doesn't load Proxyman Certificates => Please stop the project and start again.

\=> Make sure your domains are listed in  **res/xml/network\_security\_config.xml**

**3. Android Device connection is often dropped and hardly connect**

\=> Try to add **8.8.8.8** as a DNS on your current Mac Wifi.

Discussion at [https://github.com/ProxymanApp/Proxyman/issues/636](https://github.com/ProxymanApp/Proxyman/issues/636)

![](../../.gitbook/assets/Screen\_Shot\_2020-10-12\_at\_08\_18\_35.png)
