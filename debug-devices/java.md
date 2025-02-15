---
description: How to install Root CA Certificate to all Java store on macOS
---

# Java VMs

In order to intercept HTTPS traffic from Java apps, extra steps are required to install the Proxyman CA Certificate into the Java Key Store.

* Intercept Traffic from Unit Test (written by Java or Kotlin)
* Intercept Traffic from Java app or CLI

## 1. Benefit

* Proxyman provides a script to help developers automatically install Root Certificate to Java KeyStore with 1 click ✅
* Support `$JAVA_HOME`
* Support `SDKMAN`
* Support `/usr/libexec/java_home`

## 2. How to use?

### 1. Install Proxyman CA on your Mac

Before installing Proxyman CA on Java VMs, we have to install it properly on your current Mac machine.

Check out the macOS Guideline:

{% content-ref url="macos.md" %}
[macos.md](macos.md)
{% endcontent-ref %}

You can skip and start the next step if you've done this step.

## 2. Install Proxyman CA to all Java Key Stores

* Certificate Menu -> Install Certificate on Java VMs -> Run Scripts

![Run Java script](../.gitbook/assets/Screen_Shot_2022-04-08_at_15_12_49.jpg)

* The script will attempt to find the Key Store location from **JAVA\_HOME, SDKHOME,** or from **$(/usr/libexec/java\_home)** environment and install the CA Certificate if possible

<figure><img src="../.gitbook/assets/Screenshot 2025-02-15 at 14.20.51.jpg" alt=""><figcaption><p>Proxyman install the certificate to all Java Trust Store if possible</p></figcaption></figure>



{% hint style="info" %}
You can find the script at /Applications/Proxyman.app/Contents/Frameworks/ProxymanCore.framework/Versions/A/Resources/install-certificates-java.sh
{% endhint %}

{% hint style="info" %}
The script might require permission for EventKit because Proxyman triggers the script by [Apple Script](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/AppleScriptLangGuide/introduction/ASLR_intro.html) in order to install it under admin permission.
{% endhint %}

### Alternative solution

* Check out @[**yauheniprakapenka**](https://github.com/yauheniprakapenka) solution: [https://github.com/ProxymanApp/Proxyman/issues/569#issuecomment-723588490](https://github.com/ProxymanApp/Proxyman/issues/569#issuecomment-723588490) if you get the following error&#x20;

`sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target`
