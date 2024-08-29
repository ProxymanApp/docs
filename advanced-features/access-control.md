# Access Control

## 1. What's it?

It's an advanced feature, which allows you to define how Remote Devices (iPhone, Android, other computers) can connect to the Proxyman app. It's designed for enterprise users for better security.

Access via **Tools Menu** -> Proxy Setting -> Access Control.

<table><thead><tr><th width="169">Mode</th><th>Description</th></tr></thead><tbody><tr><td>Allow All</td><td>All Remote Connections can connect to Proxyman (Default).</td></tr><tr><td>Disallow All</td><td>All Remote Connections are not allow to connect to Proxyman.</td></tr><tr><td>Specify Remote Device by IP</td><td>Define which device can connect to the Proxyman app.</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/Screenshot 2023-01-23 at 09.25.40.png" alt=""><figcaption><p>Access Control UI</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-01-19 at 14.31.47.png" alt=""><figcaption><p>Prompt to allow unauthorized connections</p></figcaption></figure>

## 2. Override the Access Control mode by Command Lines

From Proxyman 4.4.0, it's possible to override the Access Control by the following CLI.

It's useful if your company would enforce the mode without using GUI.

```
$ defaults write ~/Library/Preferences/com.proxyman.NSProxy.plist accessControlModeString "allowAll"
$ defaults write ~/Library/Preferences/com.proxyman.NSProxy.plist accessControlModeString "disallowAll"
$ defaults write ~/Library/Preferences/com.proxyman.NSProxy.plist accessControlModeString "specificIP"
```
