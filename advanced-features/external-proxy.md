---
description: Proxy HTTP/HTTPS message to external Proxy server
---

# External Proxy

### 1. What's it?

Some companies have a central Proxy server, and all outgoing requests must go through to the Proxy Server in order to access the Internet.&#x20;

In this case, you might have to config Proxyman to proxy all connections to the External Proxy.

### 2. Benefits

* Navigate all traffic to your cooperated Proxy Server.
* Able to define Hosts, or Domains which bypass the External Proxy.
* Support HTTP/HTTPS/SOCKS Proxy.
* Support PAC Proxy (Automatic Proxy Configuration) (Proxyman 3.2.0+)

### 3. How to use

* **Tool** menu -> **Proxy Setting** -> **External Proxy Setting...**
* You can config **HTTP, HTTPS, or SOCKS Proxy**, which point to your external Proxy server.
* If you have a **PAC URL**, you can use it in Automatic Proxy Configuration.
* Proxyman also supports **Basic Authentication**.

![HTTP, HTTPS, SOCKS, PAC Proxy](<../.gitbook/assets/Screen Shot 2022-02-24 at 11.39.19.png>)

{% hint style="info" %}
External SOCKS Proxy with authentication is not supported.&#x20;
{% endhint %}

### 4. Bypass Proxy

* You can define hosts/domains that will be bypass the external proxy. Each host must be separated by a Comma. Wildcard (\* or ?) is supported.
* By default, Proxyam automatically bypasses all localhost traffic from the external proxy. To enable it, please check the **"Always bypass external proxies for localhost" checkbox.**

{% hint style="info" %}
Localhost traffic is traffic from your localhost, 127.0.0.1, or 0.0.0.0 with all ports.
{% endhint %}
