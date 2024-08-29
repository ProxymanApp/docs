# Firefox

In order to intercept HTTPS traffic from Firefox, it requires extra steps to install Proxyman CA into Firefox's Trust Store.

### 1. Install Proxyman CA on macOS machine

Before installing Proxyman CA on Java VMs, we have to install properly on your current mac machine.

Check out macOS Guideline:

{% content-ref url="macos.md" %}
[macos.md](macos.md)
{% endcontent-ref %}

If you've done this step, you can skip and start the next step.

### 2. Set Proxy on Firefox

* Open Firefox's Preference panel (CMD+,)
* Search Proxy and open the Proxy Setting
* Select Auto Use System Proxy or manually hardcode the Proxy IP and Port

![](../.gitbook/assets/Screen\_Shot\_2020-09-19\_at\_14\_33\_17.png)

### 3. Install Proxyman CA to Firefox

1. Open `http://proxy.man/ssl` on Firefox and download the certificate to your Download folder

{% hint style="info" %}
http://proxy.man/ssl is a local HTTP Server for strengthening the security. Please make sure the Proxyman app is open when accessing this domain.
{% endhint %}

2\. Open Firefox's Preference (CMD+,) and open View Certificate window

![](../.gitbook/assets/Screen\_Shot\_2020-06-23\_at\_10\_27\_27.png)

3\. Open the Authorities Tab and select Import button

![](../.gitbook/assets/Screen\_Shot\_2020-06-23\_at\_10\_27\_35.png)

4\. Select Proxyman CA, which you've downloaded and Trust all.

![](../.gitbook/assets/Screen\_Shot\_2020-06-23\_at\_10\_37\_52.png)

5\. Reload your page that you need intercepting. Enjoy!
