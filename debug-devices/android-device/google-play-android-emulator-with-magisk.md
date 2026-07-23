---
description: >-
  How to use Proxyman to root your Google-Play Android Emulators, so Proxyman
  can capture HTTPS from your Android app
tags:
  - new
---

# Google-Play Android Emulator with Magisk

## 1. What's it?

From Proxyman macOS 6.14.0 or later, Proxyman can do

* Override HTTPS proxy
* Install Proxyman Certificate to system store

to Google Play Android Emulator version ✅ (API 30+)

## 2. How to use it

1. Open Proxyman macOS 6.14.0 or later
2. Start your Android Emulators: Works with non Google Play Version and Google-Play version
3. Certificate Menu -> Install certificates for Androids -> Emulators
4. Check "Root Google Play Emulators with Magisk" checkbox
5. Override your Emulators
6. Done ✅

<figure><img src="../../.gitbook/assets/Screenshot 2026-07-23 at 11.37.43.png" alt="Override and Root Google Play Store with magisk"><figcaption></figcaption></figure>

## 3. How does it work?

* Proxyman bundles the Magisk.apk in the app and use it to root your Emulators with 1 click.
* You can audit at /Applications/Proxyman.app/Contents/Frameworks/ProxymanCore.framework/Versions/A/Resources/Magisk

