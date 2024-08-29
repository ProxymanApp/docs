# tvOS & watchOS

Proxyman can capture and intercept HTTP/HTTPS traffic from tvOS and watchOS.

## 1. watchOS

### Simulator

It's straightforward by following the [Proxyman iOS Simulator Guideline.](ios-simulator.md#ios-simulator-setup-guide)

### watchOS Physical Device

Follow the [iOS devices guideline](ios-device.md) to set HTTP Proxy and install the certificate to your host device.

#### Tutorial:

{% embed url="https://proxyman.io/posts/2021-09-02-intercept-https-traffic-from-watch-os-simulator" %}

## 2. tvOS

### Simulator

Fortunately, it's easy to capture traffic from the tvOS simulator. All you have to do is follow the [iOS Simulator Guideline](ios-simulator.md).

### tvOS Devices

It's quite tricky to use Proxyman on a real device.

✅ New Setup Guide (2024)

* Follow this Medium article (from Raxit Majithiya): **Setup Proxyman in a physical AppleTV** [https://medium.com/@rax/setup-proxyman-in-a-physical-appletv-bf6df86d3a28](https://medium.com/@rax/setup-proxyman-in-a-physical-appletv-bf6df86d3a28)

⚠️ Old Setup Guide

1. Follow this tutorial: [https://www.willowtreeapps.com/craft/a-how-to-guide-for-apple-tv-setup-with-charles-proxy](https://www.willowtreeapps.com/craft/a-how-to-guide-for-apple-tv-setup-with-charles-proxy)
2. Instead of using Charles Proxy, you can use Proxyman.

* Please note that Proxyman port is 9090 (default)
* Export Proxyman Certificate in the Certificate Menu -> Export
* Make sure you install & trust the Proxyman Certificate before intercepting HTTPS Traffic.

{% hint style="info" %}
If you can't set up Proxyman with watchOS or tvOS, please contact us at support@proxyman.io
{% endhint %}
