---
description: >-
  Set up Apple TV and Apple Watch simulators or real devices with Proxyman to
  capture and inspect HTTP/HTTPS requests and responses from tvOS and watchOS.
---

# tvOS & watchOS

Proxyman can capture and intercept HTTP/HTTPS traffic from tvOS and watchOS.

## 1. watchOS

### Simulator

Follow the [Proxyman iOS Simulator guide](ios-simulator.md). It works the same way for watchOS simulators.

### watchOS Physical Device

Follow the [iOS device guide](ios-device.md) to set the HTTP Proxy and install the certificate on your host device.

#### Tutorial:

{% embed url="https://proxyman.com/posts/2021-09-02-intercept-https-traffic-from-watch-os-simulator" %}

## 2. tvOS

### Simulator

Capturing traffic from the tvOS simulator is easy. Follow the [iOS Simulator guide](ios-simulator.md).

### tvOS Devices

Using Proxyman with a real Apple TV takes a few more steps.

✅ New Setup Guide (2024)

* Follow this Medium article (from Raxit Majithiya): **Setup Proxyman in a physical AppleTV** [https://medium.com/@rax/setup-proxyman-in-a-physical-appletv-bf6df86d3a28](https://medium.com/@rax/setup-proxyman-in-a-physical-appletv-bf6df86d3a28)

⚠️ Old Setup Guide

1. Follow this tutorial: [https://www.willowtreeapps.com/craft/a-how-to-guide-for-apple-tv-setup-with-charles-proxy](https://www.willowtreeapps.com/craft/a-how-to-guide-for-apple-tv-setup-with-charles-proxy)
2. Use Proxyman instead of Charles Proxy.

* Please note that the default Proxyman port is 9090
* Export the Proxyman Certificate from the Certificate menu -> Export
* Make sure you install and trust the Proxyman Certificate before intercepting HTTPS traffic.

{% hint style="info" %}
If you can't set up Proxyman with watchOS or tvOS, please contact us at support@proxyman.com
{% endhint %}

## Learn more

* [How to capture HTTP/HTTPS traffic from Apple Watch with watchOS 26](https://proxyman.com/posts/how-to-capture-https-from-apple-watch-watchOS-26)
