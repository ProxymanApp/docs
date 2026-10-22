---
description: >-
  Root Google Play Android Emulators with Magisk in one click from Proxyman, so
  Proxyman can install its certificate and capture HTTPS from your Android app.
tags:
  - new
---

# Google-Play Android Emulator with Magisk

## 1. What's it?

From Proxyman macOS 6.14.0 or later, Proxyman can:

* Override the HTTP proxy
* Install the Proxyman Certificate into the system store

on Google Play Android Emulator images ✅ (API 30+)

## 2. How to use it

1. Open Proxyman macOS 6.14.0 or later
2. Start your Android Emulators: Works with both non-Google Play and Google Play images
3. Certificate Menu -> Install Certificate on Android -> Emulators…
4. Check the "Root Google Play Emulators with Magisk" checkbox
5. Click Override All Emulators…
6. Done ✅

<figure><img src="../../.gitbook/assets/Screenshot 2026-07-23 at 11.37.43.png" alt="Proxyman Android Emulator Setup Guide with Root Google Play Emulators with Magisk checked and Override All Emulators"><figcaption></figcaption></figure>

## 3. How does it work?

* Proxyman bundles Magisk.apk in the app and uses it to root your Emulators with 1 click.
* You can audit it at /Applications/Proxyman.app/Contents/Frameworks/ProxymanCore.framework/Versions/A/Resources/Magisk

## Learn more

* [How to capture HTTPS traffic from an Android API 36 Google Play Emulator with Proxyman and Magisk](https://proxyman.com/posts/2026-08-08-capture-https-android-api-36-google-play-emulator-magisk)
