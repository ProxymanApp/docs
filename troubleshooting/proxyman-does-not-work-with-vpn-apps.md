---
description: >-
  Troubleshooting why Proxyman doesn't work with some VPN app, and how to fix it
  if possible
---

# Proxyman does not work with VPN apps

In general, VPN apps might conflict with all Web Debugging Proxy apps, includes Proxyman, Charles Proxy, Fiddler, and Wireshark.

This troubleshooting would describe what VPN services that work and do not work with Proxyman and how to fix it.

## Problems

Proxyman could not capture any HTTP/HTTPS Traffic when you're using  VPN apps.

## How to fix it in general

Basically, the VPN app would force all traffic that goes through the VPN Server instead of the Proxyman Local Server (127.0.0.1:9090). Therefore, Proxyman could not capture the traffic.

In order to fix it

* Open your VPN's Preference and try to find a text field that you can override the HTTP/HTTPS Proxy.
* If it's available, let override to the address: **127.0.0.1** at Port **9090**
* If it's not available, please google "\<Your VPN Name> config HTTP Proxy" and see how to do it.

Then, Proxyman can capture and works with your VPN app.

## List of VPNs that work with Proxyman/CharlesProxy/Fiddler

### 1. Tunnelblick

Works fine without any configuration.

### 2. FortiClient

Work fine if set HTTP Proxy to Proxyman. Please follow this guideline [https://docs.fortinet.com/document/forticlient/6.2.0/xml-reference-guide/179671/proxy-settings](https://docs.fortinet.com/document/forticlient/6.2.0/xml-reference-guide/179671/proxy-settings)

### 3. AnyConnect

* Try to set HTTP Proxy if it's available in AnyConnect's Preference
* Enter your host in "Bypass proxy settings for these Hosts & Domains" in section in System Preferences -> Network -> Wi-Fi > Advanced -> Proxies (Ref: [https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-816093447](https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-816093447))

### 4. Pulse Secure and Global Protect VPN

**Solution 1:**

First, you need to install [OpenConnect](https://casper.infradead.org/openconnect/index.html).

```bash
brew install openconnect
```

You need to obtain the installation path for `openconnect`

```
whereis -b openconnect
```

After that, don't forget to edit `/etc/sudoers`

```
sudo visudo -f /etc/sudoers 
```

Add this line and replace `<openconnect-binary-path>` with your binary path.

```
%admin ALL=(ALL) NOPASSWD: <openconnect-binary-path>
```

Now, you can connect to your secured proxy using Juniper SSL / Pulse Connect Secure protocol.

```
sudo openconnect --protocol nc -u <username> <proxy-url>
```

Once connected, launch Proxyman and it will work like a charm.

Credit: @florentmorin, from [https://github.com/ProxymanApp/Proxyman/issues/1203](https://github.com/ProxymanApp/Proxyman/issues/1203)

{% hint style="info" %}
Please consult with your Security Team before using the **sudo** command.
{% endhint %}

**Solution 2:**

It might work if we follow the following process:

1. Connect to the VPN and Verify it works
2. Open Proxyman app
3. Reset the VPN Connection

Credit: @AddictiveColors

### 5. **Viscosity**

1. Follow the documentation to [override the http-https proxy ](https://www.sparklabs.com/support/kb/article/advanced-configuration-commands/#proxy-http)on Viscosity VPN app.

Sample Configure:

```
#viscosity proxy-http localhost 9090
#viscosity proxy-https localhost 9090
```

Alternative Solution for Viscosity VPN

1. Under Advanced Tab in the Setting -> Add this to the Connection Setting:

```
dhcp-option HTTPPROXY 127.0.0.1:9090
dhcp-option HTTPSPROXY 127.0.0.1:9090
```

2. Start Proxyman -> Done

Reference: [https://stackoverflow.com/a/42515317/3127477](https://stackoverflow.com/a/42515317/3127477)

### 6. Cisco VPN

1. Disconnect your VPN
2. Open Proxyman
3. Go to Tools → Proxy Settings → Bypass Proxy Settings…
4. Add a vpn server domain (e.g., vpn.yourcompay.com etc). Tap on Done
5. Connect your VPN now

Reference: [https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-2317101771](https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-2317101771)

### Nord VPN

* For NordVPN you can use the below to set up a local http/https proxy that will router through NordVPN and then use that proxy server as an external proxy in Proxyman
* [https://github.com/edgd1er/nordlynx-proxy](https://github.com/edgd1er/nordlynx-proxy)

Credit to @seidnerj from [https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-2416373960](https://github.com/ProxymanApp/Proxyman/issues/264#issuecomment-2416373960)



## List of VPNs that do not work with Proxyman/CharlesProxy/Fiddler

#### 1. Sophos

Sophos doesn't work with all Web Debugging Proxy apps. It's a known issue from Sophos and there is no solution to fix it.

Please try to ask your Security Team to try to set the HTTP/HTTPS Proxy from Sophos.

Update: **Sophos 10.0.4** (A/V Endpoint Protection) might work with Proxyman with a new network proxy extension, but it has a known issue that causes massive CPU Spikes. It's going to fix in the upcoming EAP.

Credit: @AddictiveColors
