---
description: "Use Proxyman DNS Spoofing to send a domain to a different IP address or server while keeping the original URL and Host header unchanged."
---

# DNS Spoofing

## 1. What's it?

DNS Spoofing lets developers:

* Provide a custom DNS for particular domains
* Map a domain to a different IP address or domain

<figure><img src="../.gitbook/assets/proxyman-dns-spoofing-window.jpg" alt="Proxyman DNS Spoofing window with Enable DNS Spoofing checked and a rule that maps api.example.com to 127.0.0.1"><figcaption><p>DNS Spoofing window</p></figcaption></figure>

## 2. What is different with Map Remote?

DNS Spoofing is different from [Map Remote](map-remote.md):

* The `Host` in the request header doesn't change
* The URL doesn't change

On the other hand, Map Remote changes the Host header and the URL to the mapped values.

## 3. How to use it?

1. Open the **Tools** menu -> **DNS Spoofing…**
2. Create a new rule with the **Host Name** and the **New Remote Address**
3. Done ✅
