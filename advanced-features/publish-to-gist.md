---
description: >-
  Publish selected Proxyman requests and responses to a public or private
  GitHub Gist, so you can share them with your team using one link.
---

# Publish to Gist

## 1. What's it?

From Proxyman 2.28.0+, you can publish request and response data to GitHub Gist.

* Proxyman needs the "Read/Write Gist" permission to publish a Gist on your behalf.
* The first time, Proxyman opens the GitHub authorization page.

## 2. Benefit

* **Instantly** create a Gist from the selected requests and responses, and **quickly** share it with your colleagues.
* Supports Private and Public Gists.
* Only requires the **"Read/Write Gist"** permission. It doesn't ask for your email, username, or other permissions.
* The GitHub access token is stored securely in the Keychain.

Here is what a published Gist looks like: [example Proxyman Gist](https://gist.github.com/NghiaTranUIT/e116a60e286c917a5cbfd61aff32194c)

To choose between a private and a public Gist, open **Proxyman** -> **Settings** -> **GitHub**.

<figure><img src="../.gitbook/assets/proxyman-settings-github-gist.jpg" alt="Proxyman Settings GitHub tab with the Authorize button and options to publish a Private or Public Gist"><figcaption><p>GitHub Gist settings</p></figcaption></figure>

## 3. How to use

1. Select your requests on the main table view
2. Right-click to open the context menu -> **Export** -> **Publish to Gist…**

<figure><img src="../.gitbook/assets/proxyman-publish-to-gist-menu.jpg" alt="Proxyman right-click menu on a request with Export > Publish to Gist... highlighted"><figcaption><p>Export > Publish to Gist</p></figcaption></figure>
