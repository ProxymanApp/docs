---
description: >-
  Proxyman not capturing traffic while a VPN is on? See which VPN apps work with
  Proxyman, and how to set the HTTP proxy for FortiClient, AnyConnect and more.
---

# Proxyman does not work with VPN apps

In general, VPN apps can conflict with all web debugging proxy apps, including Proxyman, Charles Proxy, Fiddler, and Wireshark.

This page lists which VPN apps work and do not work with Proxyman, and how to fix them.

## Problems

Proxyman cannot capture any HTTP/HTTPS traffic when you're using corporate VPNs.

{% hint style="info" %}
If your VPN changes the system proxy or an app on your Mac ignores it, try [Network Extension](../advanced-features/network-extension.md). Capture works independently of the system proxy, but VPN compatibility can vary. HTTPS still needs certificate trust and [SSL Proxying](../basic-features/ssl-proxying.md).

Network Extension is BETA and requires Proxyman PRO on macOS 26 or later.
{% endhint %}

## How to fix it in general

The VPN app sends all traffic through the VPN server instead of the Proxyman local server (127.0.0.1:9090). Therefore, Proxyman cannot capture the traffic.

To fix it:

* Open your VPN's settings and look for a field where you can set the HTTP/HTTPS proxy.
* If it's available, set it to the address **127.0.0.1** and port **9090**.
* If it's not available, search for "\<Your VPN Name> config HTTP Proxy" to see how to do it.

Then, Proxyman can capture traffic while your VPN app is on.

## ✅ New Solution for iOS: Atlantis + Proxyman

* Works with any VPN.
* Capture all HTTP/HTTPS or WebSocket traffic from your iOS app.
* No need to set up a proxy or install any certificate.
* Works with iOS Simulators and iOS physical devices.

### 👉 How to use Atlantis?

* Check out the [Atlantis README](https://github.com/ProxymanApp/atlantis)
* Blog: [How to capture HTTPS traffic from an iOS app with a company VPN](https://proxyman.com/posts/capture-https-ios-app-with-company-vpn)

## List of VPNs that work with Proxyman/CharlesProxy/Fiddler

### 1. Tunnelblick

Works fine without any configuration.

### 2. FortiClient

Works fine if you set the HTTP proxy to Proxyman. Follow the [FortiClient proxy settings guide](https://docs.fortinet.com/document/forticlient/6.2.0/xml-reference-guide/179671/proxy-settings).

### 3. AnyConnect

* Try to set the HTTP proxy if it's available in AnyConnect's preferences.
* Add your VPN host to the bypass list in Proxyman: **Tools** -> **Proxy Settings** -> **Bypass Proxy Settings…**. You can also find the list in System Settings -> Network -> Wi-Fi -> Details… -> Proxies -> "Bypass proxy settings for these hosts & domains". (Ref: [GitHub issue #264](https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-816093447))

### 4. Pulse Secure and Global Protect VPN

**Solution 1:**

First, you need to install [OpenConnect](https://casper.infradead.org/openconnect/index.html).

```bash
brew install openconnect
```

Get the installation path for `openconnect`:

```
whereis -b openconnect
```

After that, edit `/etc/sudoers`:

```
sudo visudo -f /etc/sudoers 
```

Add this line and replace `<openconnect-binary-path>` with your binary path.

```
%admin ALL=(ALL) NOPASSWD: <openconnect-binary-path>
```

Now, you can connect to your secured proxy using the Juniper SSL / Pulse Connect Secure protocol.

```
sudo openconnect --protocol nc -u <username> <proxy-url>
```

Once connected, launch Proxyman. It should capture traffic as usual.

Credit: @florentmorin, from [GitHub issue #1203](https://github.com/ProxymanApp/Proxyman/issues/1203)

{% hint style="info" %}
Please consult with your Security Team before using the **sudo** command.
{% endhint %}

**Solution 2:**

It might work if you follow these steps:

1. Connect to the VPN and verify it works.
2. Open the Proxyman app.
3. Reset the VPN connection.

Credit: @AddictiveColors

### 5. **Viscosity**

1. Follow the documentation to [override the HTTP/HTTPS proxy](https://www.sparklabs.com/support/kb/article/advanced-configuration-commands/#proxy-http) in the Viscosity VPN app.

Sample configuration:

```
#viscosity proxy-http localhost 9090
#viscosity proxy-https localhost 9090
```

Alternative solution for Viscosity VPN:

1. Open the **Advanced** tab in the connection settings and add these lines:

```
dhcp-option HTTPPROXY 127.0.0.1:9090
dhcp-option HTTPSPROXY 127.0.0.1:9090
```

2. Start Proxyman. Done.

Reference: [Stack Overflow answer about Charles and VPN](https://stackoverflow.com/a/42515317/3127477)

### 6. Cisco VPN

1. Disconnect your VPN.
2. Open Proxyman.
3. Go to **Tools** -> **Proxy Settings** -> **Bypass Proxy Settings…**
4. Add your VPN server domain (for example, vpn.yourcompany.com) and click **Done**.
5. Connect your VPN again.

Reference: [GitHub issue #264](https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-2317101771)

### 7. Nord VPN

* For NordVPN, you can use the project below to set up a local HTTP/HTTPS proxy that routes through NordVPN. Then use that proxy server as an [External Proxy](../advanced-features/external-proxy.md) in Proxyman.
* [nordlynx-proxy on GitHub](https://github.com/edgd1er/nordlynx-proxy)

Credit to @seidnerj from [GitHub issue #264](https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-2416373960)

### 8. Zscaler

Follow this [workaround from the Zscaler team](https://github.com/ProxymanApp/Proxyman/issues/1307#issuecomment-1236202303).

## List of VPNs that do not work with Proxyman/CharlesProxy/Fiddler

### 1. Sophos

Sophos doesn't work with any web debugging proxy app. It's a known issue from Sophos and there is no fix for it.

Ask your Security team to set the HTTP/HTTPS proxy in Sophos.

Update: **Sophos 10.0.4** (A/V Endpoint Protection) might work with Proxyman with a new network proxy extension, but it has a known issue that causes high CPU spikes. Sophos planned to fix it in an upcoming EAP release.

Credit: @AddictiveColors
