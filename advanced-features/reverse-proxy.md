# Reverse Proxy

### 1. What's it?

Reverse Proxy would create a **local WebServer** that transparently proxies your traffic to a remote server. By doing this way, Proxyman can capture and log your traffic.

Reverse Proxy is useful when you are working on a client that doesn't support HTTP/HTTPS Proxy or the HTTP Proxy config is too complicated.&#x20;

For instance, the majority of Command-Line apps would not respect the system HTTP/HTTPS proxies, so Proxyman could not capture its traffic. To resolve it, you have to either:

* Explicitly config an HTTP/HTTPS Proxy. It's complicated and depends on the network library you are using. Check out this [troubleshooting](../troubleshooting/couldnt-see-any-requests-from-3rd-party-network-libraries.md) to know further.
* Use Reverse Proxy.

Reverse Proxy is available on Proxyman 2.29.0+.

### 2. Benefit

* Reverse Proxy feature: You can connect to Proxyman local WebServer, and it will forward your traffic to the remote host. No need to set up an HTTP/HTTPS Proxy on your client.
* Import Reverse Proxy Setting from Charles Proxy.
* Preserve Host in Header.
* Automatically select the available port when creating a new entry.
* Able to use Breakpoint, Map Local, Scripting for Reverse Proxy traffic 💯.

### 3. How to use

1. Access Reverse Proxy tool from Tools Menu -> Reverse Proxy
2. Create a new entry by entering a Remote Host and Remote Port. For the Local port, Proxyman would select automatically. You can change to a different port, but it must be available.
3. Save.
4. On your client application, change the URL to http://localhost:\<local\_port> (e.g. http://localhost:10000)
5. Make a request and inspect the traffic from the Proxyman app.

![Reverse Proxy Tool](<../.gitbook/assets/Screen Shot 2021-06-26 at 17.05.42.png>)

![Create new Reverse Proxy Entry](<../.gitbook/assets/Screen Shot 2021-06-26 at 17.05.45.png>)

{% hint style="info" %}
Proxyman would perform SSL Handshake to your Remote Server if the port is 443. Otherwise, it considers as a normal HTTP WebServer.
{% endhint %}

{% hint style="info" %}
**Preserve Host in Header Fields** allows you to preserve the original Host value. You should use it with caution because your remote server can reject the request due to a mismatched Host Value.
{% endhint %}
