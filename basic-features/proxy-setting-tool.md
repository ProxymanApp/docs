---
description: >-
  Install the Proxyman Proxy Helper Tool to change and restore the macOS system
  proxy faster, and to let guest or non-admin users capture traffic.
---

# Proxyman Proxy Helper Tool

{% hint style="info" %}
Proxyman also offers [Network Extension](../advanced-features/network-extension.md) to capture HTTP/HTTPS traffic from Mac apps that ignore proxy settings. The Helper Tool manages the system proxy; Network Extension captures supported traffic without per-app proxy setup.

Network Extension is BETA and requires Proxyman PRO on macOS 26 or later.
{% endhint %}

## What is the Proxy Helper Tool?

By default, Proxyman changes your HTTP/HTTPS proxy settings with the [networksetup](https://www.unix.com/man-page/osx/8/networksetup/) command-line tool. However, **networksetup** is slow and can delay starting or quitting the app.&#x20;

Proxyman offers a faster solution: the **Proxyman Proxy Helper Tool**. It is a macOS [Privileged Helper Tool](https://developer.apple.com/library/archive/documentation/Security/Conceptual/SecureCodingGuide/Articles/AccessControl.html#//apple\_ref/doc/uid/TP40002589-SW2) that changes the network proxy settings with **high performance**.

{% hint style="info" %}
You can see the difference by starting the app with and without the Proxy Helper Tool.
{% endhint %}

On first launch, Proxyman asks you to install the Proxy Helper Tool. You can skip it and install it later in **Settings** → **Advanced**.

<figure><img src="../.gitbook/assets/proxyman-settings-advanced-proxy-helper-tool.jpg" alt="Proxyman Settings Advanced tab showing Proxy Helper Tool installed, version 1.7.0, with an Uninstall button"><figcaption><p>Proxy Helper Tool in Settings, Advanced</p></figcaption></figure>

{% hint style="info" %}
After the installation, you can find the Helper Tool at `/Library/PrivilegedHelperTools/com.proxyman.NSProxy.HelperTool`

When Proxyman ships a new version of the Proxy Helper Tool, you need to install it again.
{% endhint %}

### Grant permission on macOS 13 Ventura or later

On macOS 13 Ventura or later, you must allow the Helper Tool in System Settings before it can work.

To grant the permission:

1. Open **System Settings** → **General** → **Login Items** (**Login Items & Extensions** on macOS 15 or later).
2. Find Proxyman and switch it ON ✅

If the permission is missing, **Settings** → **Advanced** in Proxyman shows an **Open Login Items…** button that takes you there.

<figure><img src="../.gitbook/assets/Screenshot 2022-11-20 at 21.10.43.png" alt="macOS System Settings Login Items with the Proxyman switch turned on"><figcaption><p>Grant permission to Proxyman Helper Tool</p></figcaption></figure>

### Guest or non-admin users

If you're a guest or non-admin user, the `networksetup` command fails and cannot change the HTTP/HTTPS proxy settings until you install the Proxy Helper Tool.&#x20;

The Proxy Helper Tool has the privileges to change the proxy settings for all kinds of users.

If you're a guest or non-admin user, we highly recommend installing the Proxy Helper Tool for a smoother experience.

### Uninstall the Proxy Helper Tool

You can uninstall the Proxy Helper Tool in **Settings** → **Advanced** → **Uninstall**, or delete it directly at `/Library/PrivilegedHelperTools/com.proxyman.NSProxy.HelperTool`

## Install the Proxy Helper Tool by command line

From Proxyman for macOS 4.12.0 or later, you can install the Helper Tool without the GUI:

```
sudo /Applications/Proxyman.app/Contents/MacOS/proxyman --install-privileged-components
```

## Changelog

### Version 1.6.0 (Proxyman 5.11.0 or later)

* Fixed: Proxyman can't restore the PAC URL when the app is closed

### **Version 1.5.0**

* Fixed a security vulnerability where Proxyman v1.5.0 or older (2019) could connect to the Helper Tool (v1.4.0) and override the system proxy without user consent. The fix adds constraints to verify the incoming connection: the caller must be notarized by Apple, signed with the Proxyman LLC certificate, and have Library Validation and the Force Hard flag enabled. (CVE-2023-45732)

📣 Credit to **Scott Leitch** from NCC Group.

### **Version 1.4.0**

* Comply with new macOS 13 Ventura Requirements for Helper Tool
* Show App Icon & App Name on the Login-Items

{% hint style="info" %}
On macOS Ventura or later, helper tools, launch daemons, and launch agents are listed under **Allow in the Background**, even though Proxyman only runs in the foreground.

There is an ongoing [discussion on Twitter](https://twitter.com/siracusa/status/1583914093437935616?s=46\&t=C1XB91IkDFkG697Ab8T9Dg) asking Apple to fix this in macOS.
{% endhint %}

After you install version 1.4.0, the Login Items entry might not update because macOS caches it.&#x20;

<figure><img src="../.gitbook/assets/Screen Shot 2022-10-25 at 10.00.04.png" alt="macOS Login Items entry showing an old cached name and blank icon instead of Proxyman"><figcaption><p>Login Items shows an old cached entry</p></figcaption></figure>

To fix it:

1. Open the Terminal app and run: `sfltool resetbtm`
2. Restart your Mac
3. Done

### **Version 1.3.0**

* Remember and restore to your previous Proxy Setting.

### Version 1.2.0

* Gracefully revert the HTTP Proxy Config if Proxyman crashes.

## Troubleshooting

If you see this error when installing the Helper Tool:

The operation couldn’t be completed. (CFErrorDomainLaunchd error 9.)

Follow the steps in this article: [Fix CFErrorDomainLaunchd error 9 (Tencent Cloud)](https://cloud.tencent.com/developer/article/1816504)

Related GitHub issue: [ProxymanApp/Proxyman#1113](https://github.com/ProxymanApp/Proxyman/issues/1113)
