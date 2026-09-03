---
description: >-
  Explain how to use TLS Key Logging with Proxyman to record TLS Session Keys.
  Useful for debugging with Wireshark
---

# TLS Key Logging

## 1. What's it?

Proxyman can capture TLS Key Logging and export as a txt file, so you can use it to decrypt HTTPS from Wireshark or [TCPViewer](https://tcpviewer.proxyman.com/) app

How to use it

1. Open Proxyman macOS
2. Make sure you setup the certificate on your mac correctly by following the Certificate Menu -> Install certificate for Mac -> Follow the guide to install it
3. Go to Tool menu -> TLS Key Logging
4. Enable and select the directory that the log will be saved

<figure><img src="../.gitbook/assets/Screenshot 2026-09-03 at 12.40.51.png" alt=""><figcaption></figcaption></figure>

5. Done. As soon as Proxyman capture your traffic, Proxyman will extract the TLS Key and save to the log file

* If it's from your iOS device, follow this [ios-device.md](../debug-devices/ios-device.md "mention") to set up your iPhone/iPad
* If it's from Android device -> [android-device](../debug-devices/android-device/ "mention")
* Android Emulator -> [google-play-android-emulator-with-magisk.md](../debug-devices/android-device/google-play-android-emulator-with-magisk.md "mention")
