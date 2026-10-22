---
description: >-
  Use Proxyman Network Extension to capture HTTP and HTTPS traffic from every
  app on your Mac, including apps and scripts that ignore proxy settings.
---

# Network Extension

## 1. What's it?

Network Extension captures HTTP/HTTPS traffic from apps on your Mac, including apps that ignore the system proxy.

It's built on Apple's [transparent proxy Network Extension API](https://developer.apple.com/documentation/networkextension/netransparentproxyprovider). It runs as a macOS system extension, signed with our TablePlus Inc Developer ID certificate and notarized by Apple.

It works similarly to Network Capture mode in Fiddler Everywhere and Local Capture mode in mitmproxy. You don't need to set a proxy in each app.

{% hint style="warning" %}
Network Extension is BETA and off by default. It requires Proxyman PRO, the direct Proxyman edition, and macOS 26 or later. It is not available in Setapp.
{% endhint %}

<figure><img src="../.gitbook/assets/proxyman_network_extension.jpeg" alt="Proxyman captures cURL HTTPS requests without the --proxy flag"><figcaption><p>Capture cURL requests without the --proxy flag</p></figcaption></figure>

## 2. Problem

Regular proxy mode relies on apps sending their requests through the proxy.

* Some apps and scripts ignore macOS's system proxy, so Proxyman misses their requests.
* NodeJS, Ruby, and Python libraries may need separate proxy settings, code changes, or Automatic Setup.
* Setting up each app or library by hand takes time and can lead to mistakes.

## 3. Benefits

* Capture traffic from apps and scripts that ignore proxy settings.
* Skip manual proxy setup for each app.
* Use existing tools such as Map Local, Breakpoint, and Scripting on captured requests.

## 4. How to install the Network Extension?

1. Turn on Network Extension in one of two ways:

* Open Proxyman -> **Settings** -> **Network Extension**. Turn on **Enable Network Extension**. Click **Install and Enable** if shown.

<figure><img src="../.gitbook/assets/Screenshot 2026-10-01 at 19.56.42.jpg" alt="Proxyman Settings with the Network Extension pane and the Enable Network Extension toggle"><figcaption><p>Turn on Network Extension in Settings</p></figcaption></figure>

* Or click the status bar at the top of the main window (Proxyman | Listening on ...) and turn on **Network Extension**.

<figure><img src="../.gitbook/assets/Screenshot 2026-10-01 at 19.56.31.jpg" alt="Proxyman status popover with the Recording, macOS proxy and Network Extension toggles" width="563"><figcaption><p>Turn on Network Extension from the status popover</p></figcaption></figure>

2. Open **System Settings** -> **General** -> **Login Items & Extensions**. Under **Extensions**, select **By Category** -> **Network Extensions**, then enable Proxyman.
3. When macOS asks to add the network configuration, click **Allow**.

<figure><img src="../.gitbook/assets/install_proxyman_network_extension_step_1.jpg" alt="Open General, Login Items &#x26; Extensions, By Category, then Network Extensions in System Settings"><figcaption><p>Find Network Extensions in System Settings</p></figcaption></figure>

<figure><img src="../.gitbook/assets/install_proxyman_network_extension_step_2.jpeg" alt="Enable the Proxyman toggle in Network Extensions"><figcaption><p>Allow Proxyman Network Extension</p></figcaption></figure>

4. Wait until Proxyman shows "Capturing HTTP and HTTPS from local applications."

## 5. How to use?

1. Keep Proxyman open with Network Extension enabled.
2. Network Extension now captures traffic from the apps on your Mac and sends it to Proxyman.
3. To read HTTPS content, [install and trust the Proxyman certificate](../debug-devices/macos.md), then enable [SSL Proxying](../basic-features/ssl-proxying.md) for the app or domain.
4. Make a new request from your app, browser, or script. The request appears in Proxyman.

If an app was already running before you enabled the extension, restart it to capture new connections.

To stop capture without uninstalling, turn off **Enable Network Extension** in Settings.

## 6. Troubleshooting

### SSL errors in NodeJS, Ruby, or Python

These runtimes may not trust Proxyman's self-signed certificate, even when you trust it in macOS. Network Extension captures their traffic, but certificate trust still needs setup.

Use [Automatic Setup](../automatic-setup/automatic-setup.md) to set up certificate trust for supported libraries:

1. Open Proxyman -> **Setup** -> **Automatic Setup**.
2. Click **Open New Terminal** and accept the permission prompt if needed.
3. Run your script or restart your server in that new terminal.

{% hint style="success" %}
If you're using [Automatic Setup](../automatic-setup/automatic-setup.md) or [Manual Setup](../automatic-setup/manual-setup.md), you can turn off **Enable Network Extension** in **Settings** -> **Network Extension**. Keep running your script or server in the terminal configured by that setup.
{% endhint %}

If the error continues, check the [Automatic Setup troubleshooting guide](../automatic-setup/troubleshooting.md).

## 7. How to uninstall the Network Extension?

1. Open Proxyman -> **Settings** -> **Network Extension**.
2. Click **Uninstall**, then confirm.
3. Enter your Mac password if asked, and restart your Mac if requested.

Uninstalling stops capture and closes connections using the extension. It also removes the network configuration.

## 8. Command-line

Use `proxyman-cli network-extension` to read status, install, uninstall, enable, disable, or retry. Proxyman must be open. Use `install` to install without turning capture on, or `enable` to start capture and install the extension if needed. macOS approval or a restart may still be required.

See the [Network Extension command-line guide](../command-line.md#16.-network-extension) for commands, JSON status fields, and exit codes.

## Learn more

* [Introducing Network Extension: capture Mac traffic without proxy setup](https://proxyman.com/posts/2026-10-06-introducing-network-extension)
