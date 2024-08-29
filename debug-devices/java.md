# Java VMs

In order to intercept HTTPS traffic from Java apps, it requires extra steps to install Proxyman CA Certificate into Java Key Store.

* Intercept Traffic from Unit Test (written by Java or Kotlin)
* Intercept Traffic from Java app or CLI

### 1. Install Proxyman CA on macOS machine

Before installing Proxyman CA on Java VMs, we have to install properly on your current mac machine.

Check out macOS Guideline:

{% content-ref url="macos.md" %}
[macos.md](macos.md)
{% endcontent-ref %}

If you've done this step, you can skip and start the next step.

### 2. Install Proxyman CA to all Java Key Stores

* Certificate Menu -> Install Certificate on Java VMs

![](../.gitbook/assets/Screen\_Shot\_2022-04-08\_at\_15\_12\_49.jpg)

* The script will attempt to find the Key Store location from **JAVA\_HOME** environment and install the CA Certificate if possible

![](<../.gitbook/assets/Screen Shot 2020-08-10 at 19.51.50.png>)

{% hint style="info" %}
You can find the script at /Applications/Proxyman.app/Contents/Frameworks/ProxymanCore.framework/Versions/A/Resources/install-certificates-java.sh
{% endhint %}

{% hint style="info" %}
The script might require permission for EventKit because Proxyman triggers the script by [Apple Script](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/AppleScriptLangGuide/introduction/ASLR\_intro.html) in order to install under admin permission.
{% endhint %}

### Alternative solution

* Check out @[**yauheniprakapenka**](https://github.com/yauheniprakapenka) solution: [https://github.com/ProxymanApp/Proxyman/issues/569#issuecomment-723588490](https://github.com/ProxymanApp/Proxyman/issues/569#issuecomment-723588490) if you get the following error&#x20;

`sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target`
