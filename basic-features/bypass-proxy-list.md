---
description: "Use the Proxyman Bypass Proxy List to choose domains that skip the proxy, with wildcard matching, so you can hide noise and avoid SSL pinning errors."
---

# Bypass Proxy List

## 1. Bypass Proxy List

The Bypass Proxy List helps developers to:

* ✅ Define a list of domains that **never** go through the Proxyman proxy server
* Ignore noisy traffic
* Avoid SSL errors caused by SSL Pinning when the traffic goes through Proxyman

## 2. How to use it?

1. Open the Bypass Proxy List from **Tools** → **Proxy Settings** → **Bypass Proxy Settings…**. You can also open **Tools** → **SSL Proxying List…** and click **Bypass Proxy Setting…**
2. Enter your list of domains, separated by commas. Simple wildcards (`*` and `?`) are supported.

<figure><img src="../.gitbook/assets/CleanShot 2023-06-27 at 08.28.08@2x.jpg" alt="Proxyman Bypass Proxy Settings sheet with a comma-separated list of domains over the SSL Proxying List window"><figcaption><p>Define the Bypass Proxy List</p></figcaption></figure>

## 3. How does it work?

1. As soon as Proxyman launches, it replaces your system Bypass Proxy List with the Proxyman list. You can find the system setting in **System Settings** → **Wi-Fi** → **Details…** (next to your network) → **Proxies** → **Bypass proxy settings for these hosts & domains**.
2. When you quit the app, Proxyman restores your original setting.

## Learn more

* [Can we bypass SSL Pinning?](https://proxyman.com/posts/2019-11-15-Can-we-bypass-ssl-pinning)
