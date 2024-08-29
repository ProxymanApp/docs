# Automatic Script for Android Emulator

## 1. What's it?

It's too complicated and error-prone if we manually override the HTTP Proxy, Install, and Trust Proxyman Certificate from your Android Emulator.&#x20;

Thus, Proxyman (2.10.0+) provides a built-in script to automatically perform it in a second. You can access it from **Certificate Menu -> Install Certificate on Android -> Emulator.**

{% hint style="info" %}
This Script only installs the User Certificate to the User Certificate Store, not the System Certificate Store. If you'd like to install the certificate to the System Certificate, please follow this [tutorial](https://docs.mitmproxy.org/stable/howto-install-system-trusted-ca-android/).
{% endhint %}

## 2. Benefit?

* **✅ Automatically** Override or Revert HTTP Proxy
* **✅ Automatically** Download, Install, and Trust Proxyman Certificate to the Android Emulator System.
* **✅** Less error-prone and finishes in a few clicks

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-26 at 09.49.56.png" alt=""><figcaption><p>Setup Guide for Android Emulator</p></figcaption></figure>

## 3. Android Emulator Google APIs

* Automatic Script only works with Android Emulator with the **Google APIs version**, not the Google Play Store version.

![](../../.gitbook/assets/Screen\_Shot\_2020-10-19\_at\_13\_50\_31.png)

* You can create new Android Emulators and select Google APIs in the System Image step.

![Create Emulator (Google APIs)](../../.gitbook/assets/Screen\_Shot\_2020-10-19\_at\_13\_50\_48.png)

{% hint style="info" %}
Android Emulator (Google APIs) is able to root and use the **adb** command to perform certain tasks.
{% endhint %}

## 4. How does it work?

Proxyman uses the [Android Debug Bridge](https://developer.android.com/studio/command-line/adb) (adb) to perform tasks automatically.

If you haven't installed the **adb** command yet, please follow the guideline:

1.  Install [homebrew](http://brew.sh/)

    ```
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    ```
2.  Install the **adb** command

    ```
    brew install android-platform-tools
    ```

Read more at [https://stackoverflow.com/questions/31374085/installing-adb-on-macos](https://stackoverflow.com/questions/31374085/installing-adb-on-macos)

{% hint style="info" %}
This installation step might take up to 10 minutes depending on your internet connection and the size of the homebrew repo. Please be patient when the **adb** command is installed successfully!
{% endhint %}

{% hint style="info" %}
Please make sure you **Revert Override** when you close Proxyman. Otherwise, your Android Emulator could not access the Internet.
{% endhint %}

{% hint style="info" %}
Make sure that you **remove these configs in the Release build**. If not, your HTTP/HTTPS requests can be intercepted and leak your sensitive data in the Production build.
{% endhint %}

## 5. Run the script manually

It's possible to execute the script manually in your Terminal app without granting the Automation Permission in Security & Privacy.

**Script path**: `/Applications/Proxyman.app/Contents/Frameworks/ProxymanCore.framework/Resources/install_certificate_android_emulator.sh`

### 5.1 Override HTTP Proxy and Install the Certificate

1. Open Proxyman app
2. Replace `192.168.0.1` with your current IP (You can find it under Certificate Menu -> Install Certificate on iOS -> Physical Device -> Copy the IP string)
3. Execute the following script from your Terminal app

`$ bash /Applications/Proxyman.app/Contents/Frameworks/ProxymanCore.framework/Resources/install_certificate_android_emulator.sh all 192.168.0.1 9090 ~/.proxyman/proxyman-ca.pem`

### 5.2 Only Override HTTP Proxy&#x20;

1. Open Proxyman app
2. Replace `192.168.0.1` with your current IP (You can find it under Certificate Menu -> Install Certificate on iOS -> Physical Device -> Copy the IP string)
3. Execute the following script from your Terminal app

`$ bash /Applications/Proxyman.app/Contents/Frameworks/ProxymanCore.framework/Resources/install_certificate_android_emulator.sh proxy 192.168.0.1 9090`

### 5.3 Revert HTTP Proxy&#x20;

1. Open Proxyman app
2. Execute the following script from your Terminal app

`$ bash /Applications/Proxyman.app/Contents/Frameworks/ProxymanCore.framework/Resources/install_certificate_android_emulator.sh revertProxy`
