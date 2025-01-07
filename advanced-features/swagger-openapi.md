---
description: How to export Proxyman Requests/Responses to Swagger OpenAPI 3.0 YAML format
---

# Swagger OpenAPI

## 1. OpenAPI

From Proxyman v5.14.0 or later, Proxyman can export Proxyman Requests/Responses to OpenAPI YAML format or HTML.

* Support YAML Format
* Support HTML - Swagger OpenAPI style
* Built-in in Proxyman, no need for any external dependencies.

<figure><img src="../.gitbook/assets/Screenshot 2025-01-06 at 2.37.25 PM.jpg" alt=""><figcaption><p>Export your requests/response to OpenAPI HTML Style</p></figcaption></figure>

## 2. How to use

1. Capture HTTPS requests with Proxyman. Follow the following setup guide:

* [iOS devices (iPhone, iPad)](../debug-devices/ios-device.md)
* [iOS Simulator](../debug-devices/ios-simulator.md)
* [Android devices](../debug-devices/android-device/#id-1.-android-setup-guide)
* [Android Emulator](../debug-devices/android-device/automatic-script-for-android-emulator.md)
* [macOS (Web Browser)](../debug-devices/macos.md)

Verify Proxyman can capture & decrypt your HTTPS Requests/Responses

<figure><img src="../.gitbook/assets/CleanShot 2025-01-06 at 2 .47.34@2x.jpg" alt=""><figcaption><p>Capture your HTTPS Request/Response</p></figcaption></figure>

2. Select your requests on the main table -> Right-Click -> Export -> OpenAPI -> Select either OpenAPI YAML or OpenAPI HTML
3. Done :white\_check\_mark:
