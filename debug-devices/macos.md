---
description: How to install Certificate and debug HTTPS contents in macOS device.
---

# macOS

## Install Certificates on macOS

In order to intercept encrypted HTTPS messages (Request or Response), you have to install **Proxyman CA Certificate** on your current machine. This step is mandatory for iOS, Android devices, iOS simulators, Java VMs, and Firefox too.

You can install the Proxyman CA Certificate by navigating to

* **Certificate** menu -> **Install Certificate on this Mac**...

{% hint style="info" %}
The Proxyman Certificate is a self-signed certificate, which is generated in your machine. Proxyman never stores or transmits any personal data to Proxyman's server or 3rd-party.

Please check out the [Privacy Statement](https://proxyman.io/privacy) to understand what Proxyman obtains or not.

If you'd like to manually generate a Certificate on your machine then adding to Proxyman. Please check out the [Custom Certificate Doc](../advanced-features/custom-certificates.md#6-how-to-generate-self-signed-certificates-for-custom-root-certificate-that-comply-with-new-apples-security-requirements)
{% endhint %}

{% hint style="info" %}
Proxyman's certificate is store locally at **\~/.proxyman** or **\~/Library/Application Support/com.proxyman.NSProxy/certificates/**
{% endhint %}

## 1. Automatic mode

Proxyman could **automatically** install & trust the Certificate in Keychain by following the instruction in the following screenshot.&#x20;

It's convenient for the majority of users and we can start debugging now.

![Install & trust Proxyman Certificacte](../.gitbook/assets/proxyman\_install\_ca\_certificate.jpg)

{% hint style="info" %}
**Automation mode** requires **Root Privileges** to perform the installation script. If you're not sure, please consider using Manual mode.
{% endhint %}

### How does it work?

In automatic mode, Proxyman will automatically perform two steps:

1. Generate a local Proxyman Certificate at `~/.proxyman/proxyman-ca.pem`
2. Install & Trust the certificate to System Keychain Access. It requires Root Privileges to execute the following CLI:&#x20;

`sudo security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.keychain ~/.proxyman/proxyman-ca.pem`

## 2. Manual Mode

Proxyman also offers more freedom for super-users who need to install the certificate on their behalf.&#x20;

You can select one of the following approaches:

### 2.1 Generate certificate

* **Generate and Add**: Proxyman will locally generate the certificate and add it to Keychain, but not Trust automatically.
* **Add your Custom Certificate**: Proxyman will open Custom Certificate and help you **manually** generate a certificate by using the **OpenSSL** command line. This feature intends for advanced users.

{% hint style="info" %}
Make sure you select the "System Keychain" when adding the certificate to Keychain Access.
{% endhint %}

![Manually install Proxyman Certifiacte](../.gitbook/assets/proxyman\_install\_manual.jpeg)

{% hint style="info" %}
If you would like to manually generate a Root Certificate that works with Proxyman, please check out the [Custom Certificate Doc](../advanced-features/custom-certificates.md#6-how-to-generate-self-signed-certificates-for-custom-root-certificate-that-comply-with-new-apples-security-requirements)
{% endhint %}

### 2.2 Trust Proxyman Certificate on Keychain Access

Make sure that your machine trusts Proxyman Certificate properly.&#x20;

* Open **Keychain Access** app -> Search **Proxyman CA** -> Double Click on the certificate -> Expand the Trust Section -> Select "Always Trust" **->** Quit and Save the change.

{% hint style="info" %}
If you've done it correctly, Proxyman will display " ✅ Installed and Trusted" status.
{% endhint %}

If you are not sure how to trust the certificate on the Keychain Access app. You can open the Terminal app and execute the command:

`sudo security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.keychain ~/.proxyman/proxyman-ca.pem`

{% hint style="info" %}
Make sure that you **Delete the Proxyman Certificate in Keychain app** if you're not using Proxyman anymore. If not, anyone who has the Proxyman Certificate can intercept your HTTP/HTTPS requests from your macOS machine.
{% endhint %}
