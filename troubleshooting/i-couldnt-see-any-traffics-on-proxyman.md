---
description: "Troubleshoot missing traffic in Proxyman by checking proxy settings, recording, filters, VPN conflicts, and cached requests."
---

# I couldn't see any traffics on Proxyman

An empty request list usually means traffic is not reaching Proxyman, recording is paused, or a filter hides the requests. Check the proxy and capture settings first, then test for VPN conflicts and cached responses.

### 1. Problems

* After launching the app, the request list is empty
* There are no requests captured by Proxyman?
* I don't see any requests on the app
* I can see some request on my Mac, but no request on my remote devices (iOS, Android)

{% hint style="info" %}
For remote devices (iOS or Android), please check out this [troubleshoot](my-ios-devices-couldnt-connect-to-proxyman-via-proxy.md).
{% endhint %}

![](../.gitbook/assets/Screen\_Shot\_2020-04-26\_at\_09\_48\_10.png)

### 2. Solution

Work through these checks in order, making a fresh request after each change:

1. **Check the proxy:** Confirm that your client uses the computer and port where Proxyman is listening. For local Mac traffic, check the HTTP and HTTPS system proxy values below. For an iOS or Android device, use the computer IP address from its Proxyman setup guide.
2. **Check capture settings:** Make sure recording is enabled and clear any active request filters. If HTTP appears but HTTPS cannot be read, verify certificate trust and [SSL Proxying](../basic-features/ssl-proxying.md) for the domain.
3. **Check VPN interaction:** Temporarily disconnect the VPN if possible, then recheck proxy settings and repeat the request. Some VPN clients overwrite the proxy configuration.
4. **Check cached requests:** Repeat an action that sends a new network request, or try the No Caching tool described below. A response served entirely from the app cache will not pass through the proxy.

The sections below explain the proxy, VPN, helper-tool, and caching checks in more detail.

### 2.1 Turn OFF all VPN apps on your Mac machine

Some VPN apps accidentally revert the HTTP Proxy in Network as soon as Proxyman overrides it. As a result, HTTP Traffic won't go through Proxyman port at 9090.

Close all VPN app if possible and relaunch Proxyman

### 2.2. Double-check HTTP Proxy in Network

Proxyman would override or revert the HTTP Proxy at the launch time or exit, but some apps could revert back.

Let open System Preference -> Network -> Wifi -> Proxies tab:

* Check the **Web Proxy (HTTP)** and **Secure Web Proxy (HTTPS)**
* Make sure the port is the same as the Proxyman port
* IP is **127.0.0.1**

Save and check the requests on Proxyman

![](<../.gitbook/assets/Screen Shot 2020-04-26 at 09.54.53.png>)

### 2.3 Install Proxyman Helper Tool

By default, Proxyman attempts to override the system HTTP Proxy by using `networksetup` CLI, but it might be failed in certain scenarios.

\=> Let's try to install Proxyman Helper Tool. This tool will override the system HTTP Proxy properly. Open Proxyman Settings -> Advanced -> Install Helper Tool

![](../.gitbook/assets/Screen\_Shot\_2020-10-12\_at\_08\_24\_05.png)

### 2.4 Some HTTP/HTTPS Requests are missing from Proxyman

Alamofire or URLSession might use the cached response for your request. As a result, the actual request doesn't hit the server. Thus, Proxyman could not capture and display it on the app.

Solution:&#x20;

* Disable the cache mechanism on URLSession or Alamofire.
* Use the [No Caching Tool](../advanced-features/no-caching.md) (⌥⌘N)
