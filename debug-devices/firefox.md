---
description: How to capture HTTPS Reqyests/Responses from Firefox Browser with Proxyman
---

# Firefox

## ✅ New Solution (Proxyman v5.19.0 or later - recommended)

With Proxyman v5.19.0+, Proxyman can capture HTTPS Requests/Responses from Firefox with 1-click setup.

1. Go to Setup Menu -> Automatic Setup
2. On the Web Browser Section -> Click the ⬇️ Arrow Button -> Select Firefox

<figure><img src="../.gitbook/assets/Screenshot 2025-04-28 at 09.53.27.jpg" alt=""><figcaption><p>How to capture HTTPS Reqyests/Responses from Firefox Browser with Proxyman</p></figcaption></figure>

3. New Firefox instance will open
4. ✅ Done. All traffic from Firefox will be captured by Proxyman

This setup will make Firefox or Google Chrome:

* Auto set Proxyman to Proxyman
* Auto install & trust Proxyman Certificate

{% hint style="success" %}
Works with Google Chrome and Firefox
{% endhint %}

## ❌ Old Solution (Proxyman v5.18.0 or ealier)

In order to intercept HTTPS traffic from Firefox, it requires extra steps to install Proxyman CA into Firefox's Trust Store.

### 1. Install Proxyman CA on macOS machine

Before installing Proxyman CA on Java VMs, we have to install it properly on your current machine.

Check out macOS Guidelines:

{% content-ref url="macos.md" %}
[macos.md](macos.md)
{% endcontent-ref %}

If you've done this step, you can skip to the next step.

### 2. Set Proxy on Firefox

* Open Firefox's Preferences panel (CMD+,)
* Search Proxy and open the Proxy Settings
* Select Auto Use System Proxy or manually hardcode the Proxy IP and Port

![](../.gitbook/assets/Screen_Shot_2020-09-19_at_14_33_17.png)

### 3. Install Proxyman CA to Firefox

1. Open `http://proxy.man/ssl` on Firefox and download the certificate to your Download folder

{% hint style="info" %}
http://proxy.man/ssl is a local HTTP Server for strengthening the security. Please make sure the Proxyman app is open when accessing this domain.
{% endhint %}

2\. Open Firefox's Preferences (CMD+,) and openthe  View Certificate window

![](../.gitbook/assets/Screen_Shot_2020-06-23_at_10_27_27.png)

3\. Open the Authorities Tab and select the Import button

![](../.gitbook/assets/Screen_Shot_2020-06-23_at_10_27_35.png)

4\. Select Proxyman CA, which you've downloaded and Trust all.

![](../.gitbook/assets/Screen_Shot_2020-06-23_at_10_37_52.png)

5\. Reload the page that you need to intercept. Enjoy!
