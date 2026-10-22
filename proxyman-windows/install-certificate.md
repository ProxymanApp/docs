---
description: >-
  Install and trust the Proxyman CA certificate on Windows 10 and 11, with the
  automatic script or by hand, so Proxyman can decrypt HTTPS traffic.
---

# Install Certificate

## Install Certificates on Windows

To intercept encrypted HTTPS messages (Request or Response), you have to install the **Proxyman CA Certificate** on your Windows machine.

You can install the Proxyman CA Certificate from

* **Certificate** menu -> **Install Certificate on this Windows**...

{% hint style="info" %}
The Proxyman Certificate is a self-signed certificate, which is generated on your machine. Proxyman never stores or sends any personal data to Proxyman's server or any 3rd party.

Please check out the [Proxyman Privacy Statement](https://proxyman.com/privacy) to see what data Proxyman collects.

If you'd like to generate a Certificate on your machine by hand and then add it to Proxyman, please check out the [Custom Certificate Doc](../advanced-features/custom-certificates.md#6-how-to-generate-self-signed-certificates-for-custom-root-certificate-that-comply-with-new-apples-security-requirements)
{% endhint %}

## 1. Automatic mode

<figure><img src="../.gitbook/assets/Screenshot 2023-01-23 at 09.38.09.png" alt="Proxyman for Windows Install Certificate dialog showing the certificate as Installed and Trusted"><figcaption><p>Auto install the certificate on Windows machine</p></figcaption></figure>

Proxyman provides an automatic script to install and trust the Proxyman CA Certificate in the System.

* Certificate Menu -> Install Certificate for this Windows -> Click on the "Install & Trust" button
* Click YES on the System Prompt

<figure><img src="../.gitbook/assets/Screenshot_2023-01-23_at_09_41_41.jpg" alt="Windows User Account Control prompt for Windows Command Processor with the Yes button"><figcaption><p>Grant permission to run the Automatic Script</p></figcaption></figure>

### Why do I need to grant permission?

Behind the scenes, Proxyman runs the following command as Administrator:

```bash
$ certutil -addstore "Root" <Certificate_Path>
```

{% hint style="info" %}
[certutil](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/certutil) is a built-in Windows command line to manage the certificate.
{% endhint %}

## 2. Manual Mode

If you don't have permission to run the script, please follow these steps:

1. Close Proxyman
2. Find a Proxyman CA Certificate at "C:\Users\\\<your\_username>\AppData\Roaming\Proxyman\certificate\certs\ca.cer"
3. Double-click to open it
4. Install Certificate -> Select "Current User" -> Select "Place all certificates in the following store" -> "Browse..." -> Select "Trusted Root Certification Authorities" -> OK

<figure><img src="../.gitbook/assets/212792551-e3875685-294b-46b4-b563-b3c7051fb29a.jpg" alt="Windows Certificate Import Wizard placing the certificate in the Trusted Root Certification Authorities store"><figcaption><p>Steps to install the certificate</p></figcaption></figure>

5\. Select Next -> Finish

6\. Select "YES" on the System Prompt.

