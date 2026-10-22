---
description: >-
  Record TLS session keys with Proxyman TLS Key Logging and save them to a
  file, so you can decrypt HTTPS traffic in Wireshark or TCP Viewer.
---

# TLS Key Logging

## 1. What's it?

Proxyman can log TLS session keys and save them to a txt file, so you can decrypt HTTPS traffic in Wireshark or the [TCP Viewer](https://tcpviewer.proxyman.com/) app.

## 2. How to use it

1. Open Proxyman for macOS
2. Make sure the Proxyman certificate is installed on your Mac: open the **Certificate** menu -> **Install Certificate on this Mac…** and follow the guide
3. Open the **Tools** menu -> **TLS Key Logging…**
4. Check **Enabled TLS Key Logging**, click **Select Folder…** to choose where to save the log file, then click **Save**

<figure><img src="../.gitbook/assets/Screenshot 2026-09-03 at 12.40.51.png" alt="Proxyman TLS Key Logging sheet with logging enabled and the Desktop folder selected as the file path"><figcaption><p>TLS Key Logging settings</p></figcaption></figure>

5. Done. When Proxyman captures your traffic, it extracts the TLS keys and saves them to the log file.

* For an iOS device, follow [ios-device.md](../debug-devices/ios-device.md "mention") to set up your iPhone/iPad
* For an Android device, follow [android-device](../debug-devices/android-device/ "mention")
* For an Android Emulator, follow [google-play-android-emulator-with-magisk.md](../debug-devices/android-device/google-play-android-emulator-with-magisk.md "mention")
