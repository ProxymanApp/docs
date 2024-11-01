---
description: >-
  How to set up iOS / iPad Simulator with Proxyman to capture HTTP/HTTPS
  Requests/Response
---

# iOS Simulator

In order to capture the HTTP/HTTPS message from your iOS Simulator devices, please navigate to:

* **Certificate** **Menu** -> **Install Certificate on iOS -> Simulators**

## 1. iOS Simulator Setup Guide

![Automatically install the Certificate to iOS Simulators](<../.gitbook/assets/Screen Shot 2022-07-11 at 08.15.26.png>)

{% hint style="info" %}
It works for iOS, iPadOS, tvOS and watchOS.
{% endhint %}

The following photo describes three steps:

1. Install **Root Proxyman Certificate** on your machine: You can follow the [macOS Guide](macos.md).
2. Install Proxyman Certificate to all available simulators, which you have opened at least one time.
3. **Reset the Simulator**: Proxyman tries to reset all simulators, so it will load the new Certificate.

{% hint style="info" %}
From Proxyman 2.19.0+, Proxyman uses the [simctl](https://nshipster.com/simctl/) command line to perform tasks.&#x20;

**simctl** is built-in on your installed Xcode, which is more modern and reliable than the legacy approach (Use Python custom scripts).
{% endhint %}

{% hint style="info" %}
This step only installs on Simulators, which you have open at least one time

For instance, if you would like to debug on iPhone X Simulator, please make sure to **open** the iPhone X Simulator first, then **install** the Certificate in Step 2&#x20;
{% endhint %}

### Xcode Preview (SwiftUI)

If you're using Xcode Preview for SwiftUI, you can install the certificate into the Xcode Preview Simulator by following:

1. Open Xcode with Previewer Mode (SwiftUI).
2. Open Proxyman -> Certificate Menu -> Install for iOS -> Simulator
3. Click on the Advanced button -> Install for Xcode Preview

You can read more at: [https://github.com/ProxymanApp/Proxyman/issues/1568#issue-1610877870](https://github.com/ProxymanApp/Proxyman/issues/1568#issue-1610877870)

### Manually Install

In Proxyman v4.16.0 or later, you can manually install the certificate to your iOS Simulator in case the Automatic Solution doesn't work.

1. Certificate Menu -> Install Certificates for iOS -> Simulators
2. In Step 2, click on the ↓ button (Next to the Prepare Simulators button) -> Install Manually…

<figure><img src="../.gitbook/assets/Screenshot 2024-11-01 at 20.14.39.jpg" alt=""><figcaption><p>Install certificate manually</p></figcaption></figure>

3. Drag and drop the certificate to your iOS Simulator

<figure><img src="../.gitbook/assets/Screenshot 2024-01-07 at 14.43.13.png" alt="" width="563"><figcaption><p>Manually Install the certificate</p></figcaption></figure>

4. Open your iOS Simulator -> Setting app -> General -> About -> Certificate Trust Setting -> Find Proxyman CA Certificate and switch it ON
5. Done

## 2. Troubleshooting

### 1. Unable to install the Certificate

If you get errors when clicking on Step 2, please open Xcode -> Preferences -> Location tabs -> Select your Xcode in the Command Line Tools.

![Make sure you have the Xcode Command Line](../.gitbook/assets/Screen\_Shot\_2022-07-11\_at\_08\_12\_33.png)

### 2. Get SSL Error from HTTPS Response

* Opening the Setting app -> General -> About -> Certificate Trust Settings and verifying that Proxyman Certificate is installed and trusted.

![Proxyman Certificate is installed and trusted properly](<../.gitbook/assets/Screen Shot 2021-03-05 at 13.32.25.png>)

If it's not installed:

* Open the iOS Simulator Setup (Certificate Menu -> Install Certificate on iOS -> Simulator) and click on the 2nd button.
* Or Try the following step to manually install the Certificate.

### 3. Some HTTP/HTTPS Requests are missing from Proxyman

Alamofire or URLSession might use the cached response for your request. As a result, the actual request doesn't hit the server. Thus, Proxyman could not capture and display it on the app.

Solution:&#x20;

* Disable the cache mechanism on URLSession or Alamofre.
* Use the [No Caching Tool](../advanced-features/no-caching.md) (⌥⌘N)

## Manually Install the Certificate by exporting the certificate

If you cannot install the certificate, you can **manually** do it:

1. Open Proxyman -> Certificate Menu -> Export -> Root Certificate as DER -> Save to Desktop Folder
2. Open the Simulator **drag the certificate and drop it** on the Simulator screen
3. Open Setting app (on the Simulator) -> General -> Device Management -> Select the Certificate -> Install
4. Setting app -> General -> About -> Certificate Trust Settings and verifying that Proxyman Certificate is installed and trusted.
5. Done ✅

### Tutorial

See detailed steps to [debug an application on iOS Simulator ](https://proxyman.io/blog/2019/07/Debugging-on-iOS-Simulator-with-Proxyman.html)with Proxyman
