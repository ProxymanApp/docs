---
description: Explain how to set up your Electron JS App, so Proxyman can capture HTTP/HTTPS
---

# ElectronJS

## 1. Problem

Many ElectronJS apps are unaware of System Proxy; it doesn't respect the System HTTP Proxy, so Proxyman can't capture HTTP/HTTPS from this app :x:

## 2. Solution

From Proxyman macOS 6.7.0 or later

* Capture HTTP/HTTPS from ElectronJS app
* 1-click to set up
* No modify the source code, it just works :white\_check\_mark:

## 3. How to use

1. Start Proxyman app: Make sure you've already installed & trusted Proxyman Certificate to your Mac. If not, you can follow the guide from the Certificate Menu -> Install Certificate on this Mac -> Automatic Tab
2. Open the Setup Menu -> Automatic Setup
3. Click on the "Select Electron App" button and select the app you'd like to capture (Make sure to kill your Electron App first)
4. Done :white\_check\_mark:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-02 at 16.11.10.jpg" alt="Captuer HTTP from Electron App with Proxyman"><figcaption></figcaption></figure>



