---
description: >-
  Use the Proxyman Block List to block or hide requests by domain, wildcard,
  regex, or app, so ads, analytics, and noisy pings stay out of your session.
---

# Block List

## 1. What's it?

The Block List Tool is useful when you would like to **block or hide** certain domains during a debugging session.

For instance, you can use Block List in the following situations:

* Block all ad requests from particular domains
* Block all analytics requests that flood your workspace
* Block all annoying ping requests from your app, so fewer requests show in Proxyman
* Hide analytics traffic from your website without blocking it

For all blocked domains in the Block List, Proxyman **drops the connection.**

<figure><img src="../.gitbook/assets/Screenshot 2025-09-05 at 21.11.17.png" alt="Proxyman Block List window with rules that block a wildcard domain, Google Chrome and WhatsApp"><figcaption><p>Block certain requests by domain or client</p></figcaption></figure>

## 2. Block Actions

Block List supports a few block actions to suit your needs:

<table><thead><tr><th width="238.87890625">Block Action</th><th>Description</th></tr></thead><tbody><tr><td>Block &#x26; Hide Request</td><td>Matched requests are blocked and don't show in the app.</td></tr><tr><td>Block &#x26; Display Requests</td><td>Matched requests are blocked, but the blocked requests still show in the app.</td></tr><tr><td>Hide, but not Block</td><td>Only hides the matched requests without blocking them. Useful when you want to hide annoying requests but not block them.</td></tr></tbody></table>

![Proxyman Block List rule editor with a wildcard matching rule and the Block and Hide Request action](<../.gitbook/assets/Screen Shot 2022-01-10 at 14.43.38.png>)

## 3. How to use it?

* **Tools** Menu -> **Block List**
* Right-click on the requests or domains -> **Tools** -> **Block List...**

{% hint style="success" %}
**⌥⌘\[** to quickly open the Block List window
{% endhint %}

## 4. Block all traffic from a given App

* On Proxyman macOS 5.24.0 or later, you can select an app and block all of its traffic. In the rule editor, click **Select App…** next to **Block App**.

<figure><img src="../.gitbook/assets/Screenshot 2025-09-02 at 10.08.23.jpg" alt="Proxyman Block List rule editor with Block App set to Dropbox and the Block and Hide Request action"><figcaption><p>Block all traffic from an app</p></figcaption></figure>
