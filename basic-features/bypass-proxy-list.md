# Bypass Proxy List

## 1. Bypass Proxy List

Bypass Proxy Lis helps developers to:

* ✅ Define a list of domains that **never** go to the Proxyman Proxy Server
* Ignore some noised traffic
* Avoid SSL Error due to SSL Pinning when proxying to the Proxyman app.

## 2. How to use it?

2. Open the Bypass Proxy List in Tools Menu -> SSL Proxying List -> Bypass Proxy List
3. Enter your list of domains (separated by Comma, support simple wildcard)

<figure><img src="../.gitbook/assets/CleanShot 2023-06-27 at 08.28.08@2x.jpg" alt=""><figcaption><p>Define a list of bypass proxy list</p></figcaption></figure>

## 3. How does it work?

1. As soon as the Proxyman app is launched, Proxyman will override your system Bypass Proxy List with Proxyman List. You can find the system setting in System Setting -> Wi-Fi -> Your Wifi hotspot ->  Details… -> Proxy -> Bypass Proxy List
2. When the app is closed -> Proxyman will revert to your original setting.
