---
description: >-
  Set up SSL Proxying in Proxyman to decrypt and inspect HTTPS traffic from
  selected apps and domains, using host names or wildcard rules.
---

# SSL Proxying

SSL Proxying tells Proxyman which apps and domains to decrypt, so you can read their HTTPS requests and responses in plain text.

For HTTP/2 traffic on macOS, also enable **Use HTTP/2** in Settings. See the [HTTP/2 guide](http2.md) for setup and protocol checks. Certificate trust and SSL Proxying are still required to inspect HTTPS content.

## Video

{% embed url="https://proxyman.com/videos/capture-http-https-traffic" %}
Capture HTTP and HTTPS traffic with Proxyman
{% endembed %}

## 1. SSL Proxying List

The SSL Proxying List is a list of domains or apps whose SSL connections Proxyman should decrypt. It lets you inspect HTTPS requests and responses in plain text.

### Include List and Exclude List

You can define rules for:

* **Include List**: Intercept the traffic from apps/domains in the Include List
* **Exclude List**: Ignore all traffic from apps/domains in the Exclude List

![Proxyman SSL Proxying List window with an Include List and an Exclude List of apps and domains](../.gitbook/assets/ssl\_proxying.png)

{% hint style="info" %}
Press ⌘⌥P to quickly open the SSL Proxying List.
{% endhint %}

### Apps / Domains / Wildcards

Proxyman supports several formats to define a rule:

* **By app**: Intercept all traffic from this app
* **By domain**: Intercept all traffic from this domain
* **Wildcard**: Intercept traffic from every domain that matches the wildcard

For example:

| Wildcard                    | Description                                                |
| --------------------------- | ---------------------------------------------------------- |
| \*                          | Decrypt ALL HTTPS traffic                                  |
| \*.domain.com, \*.apple.com | e.g. v1.domain.com, data.domain.com, health.apple.com, ... |
| v?.domain.com               | e.g. v1.domain.com, v2.domain.com, ...                     |

{% hint style="info" %}
You must set up the Proxyman Certificate before intercepting any HTTPS requests. Follow the [macOS setup guide](../debug-devices/macos.md) to install and trust the certificate.
{% endhint %}

### How to enable SSL Proxying on a particular domain or app

* Right-click the app or domain in the left panel → **Enable SSL Proxying**

<figure><img src="../.gitbook/assets/domain.jpeg" alt="Proxyman sidebar context menu on a domain with Enable SSL Proxying highlighted"><figcaption><p>Add a domain to the SSL Proxying List</p></figcaption></figure>

* Right-click the request in the main table → **Enable SSL Proxying**
* Select the request and enable SSL Proxying in the Response panel.

<figure><img src="../.gitbook/assets/2.jpeg" alt="Proxyman Response panel for an encrypted HTTPS response with buttons to enable SSL Proxying"><figcaption><p>Enable the entire app or a single domain</p></figcaption></figure>

## Learn more

* [Can we bypass SSL Pinning?](https://proxyman.com/posts/2019-11-15-Can-we-bypass-ssl-pinning)
