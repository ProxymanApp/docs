---
description: "Add custom root, server, and client certificates to Proxyman for SSL pinning and mutual TLS, and generate a self-signed root certificate Apple trusts."
---

# Custom Certificates

## 1. What's it?

Proxyman supports custom **Root Certificates**, **Server Certificates**, and **Client Certificates**. You can add your own certificates, and Proxyman uses them to set up the SSL connection between your clients, your servers, and the Proxyman app.

| Custom Certificate Type | Purpose                                                                                           | How Proxyman uses                                         |
| ----------------------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| **Server Certificate**  | For intercepting HTTPS Traffic from clients that use SSL-Pinning                                 | Use this certificate for SSL-Handshake to your Clients    |
| **Client Certificate**  | For intercepting HTTPS Traffic from clients that use Mutual Authentication                        | Use this certificate for SSL-Handshake to specific Server |
| **Root Certificate**    | For intercepting HTTPS Traffic from clients and servers without using local Proxyman certificates | SSL Handshake for both clients & servers                  |

![Proxyman Custom Certificates window with a custom root certificate that is installed and trusted](<../.gitbook/assets/Screen Shot 2020-09-09 at 15.52.42.png>)

{% hint style="info" %}
The Proxyman Root Certificate is generated locally on your Mac. You can also generate your own root certificate and add it to Proxyman. See [how to generate a self-signed root certificate](custom-certificates.md#6-how-to-generate-self-signed-certificates-for-custom-root-certificate-that-comply-with-new-apples-security-requirements).
{% endhint %}

## 2. Certificate Formats

Proxyman accepts the following formats:

| Custom Certificate | PEM or DER    | PKCS #12 (p12) |
| ------------------ | ------------- | -------------- |
| Root Certificate   | Not Supported | Supported      |
| Client Certificate | Supported     | Supported      |
| Server Certificate | Supported     | Supported      |

* PKCS #12 (p12).
* PEM or DER Private Key and Certificate file.

{% hint style="info" %}
- Proxyman automatically detects the format of the Private Key and Certificate file (PEM or DER).
- Proxyman asks for the password when you import an encrypted Private Key or PKCS #12 file.
- All passphrases are securely stored in Proxyman Keychain.
{% endhint %}

{% hint style="info" %}
If your certificates are in a format that Proxyman doesn't support, convert them to p12 or PEM/DER before importing.
{% endhint %}

## 3. Certificate Requirement on macOS 10.15+ and iOS 13+

If you use a custom Root Certificate or Server Certificate on macOS 10.15 or later, or iOS 13 or later, the SSL handshake can fail in Safari or on iOS devices unless the certificate meets these requirements:

* RSA keys must use a key size of 2048 bits or more
* The hash algorithm must be in the SHA-2 family
* The DNS name of the server must be in the Subject Alternative Name (SAN). The Common Name (CN) is no longer trusted
* The certificate must be valid (today is between the Not Before and Not After dates)
* TLS server certificates must contain an ExtendedKeyUsage (EKU) extension containing the **id-kp-serverAuth** OID.

Read more: [Requirements for trusted certificates in iOS 13 and macOS 10.15](https://support.apple.com/en-us/HT210176)

{% hint style="info" %}
If this is too complicated, let Proxyman do it for you. Open the **Certificate** menu -> **Install Certificate on this Mac…** -> select the **Automatic** tab.
{% endhint %}

## 4. Common issues

| Problem                                                | Solution                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Private Key and Certificate are not matched            | Try different certificates and private keys and make sure they match                                                                                                                                                                                                                                     |
| Get SSL Handshake Error for custom certificates        | <ul><li>Try to add the custom Certificate to System Keychain and Trust it</li><li>Certificate doesn't match the requirement from macOS => Read <a href="custom-certificates.md#3-certificate-requirement-on-macos-10-15-and-ios-13">section 3</a></li><li>Check the expiry date of the Certificate</li></ul> |
| Could not import certificate due to invalid passphrase | Ask your team lead for the correct passphrase to open the encrypted Private Key or P12 file                                                                                                                                                                                                             |

## 5. How to use

* Open the **Certificate** menu -> **Add Custom Certificates…**

![Proxyman Certificate menu with Add Custom Certificates selected](<../.gitbook/assets/Screen Shot 2021-07-31 at 20.21.35.png>)

## 6. How to generate self-signed certificates for Custom Root Certificate that comply with new Apple's Security Requirements

Because of [Apple's requirements from iOS 13 and macOS Catalina (10.15)](custom-certificates.md#3-certificate-requirement-on-macos-10-15-and-ios-13), you need some extra configuration to generate a self-signed certificate that works.

Follow these steps:

1. Create a `cert.config` file in your **Desktop** folder

```
[ ca ]
default_ca    = CA_default
[ CA_default ]
default_md    = sha256
[ v3_ca ]
subjectKeyIdentifier=hash
authorityKeyIdentifier=keyid:always,issuer
basicConstraints = critical,CA:true
keyUsage=critical,keyCertSign
extendedKeyUsage = serverAuth,clientAuth
[ req ]
prompt = no
distinguished_name    = req_distinguished_name
[ req_distinguished_name ]
C=US
L=US
O=Proxyman LLC
CN=proxyman.dev
OU=Proxyman
```

* Update the values of the C, L, O, CN, and OU parameters.

2\. Generate an RSA key in the Terminal app. (Replace **your\_password** with any password, e.g. 123456)

```bash
cd ~/Desktop
openssl genrsa -aes256 -passout pass:your_password -out key.pem 2048
```

3\. Generate the self-signed certificate and private key. (Replace **your\_password** with the password in step 2)

```
openssl req -x509 -new -nodes -passin pass:your_password -config cert.config -key key.pem -sha256 -extensions v3_ca -days 825 -out root-ca.pem
```

4\. Convert to p12 format. (Replace **your\_password** with the password in step 2)

```
openssl pkcs12 -export -legacy -out root-ca.p12 -in root-ca.pem -inkey key.pem -passin pass:your_password -passout pass:your_password
```

5\. You now have a **root-ca.p12** file. Move on to the next step.

{% hint style="info" %}
If you can't import your custom certificate on macOS 14 (OpenSSL v3) or later, use the \`-legacy\` flag in step 4.

Reference: [MAC verification failed during PKCS12 import (Stack Overflow)](https://stackoverflow.com/questions/70431528/mac-verification-failed-during-pkcs12-import-wrong-password-azure-devops)
{% endhint %}

## 7. Import as a Custom Root Certificate

1. Open the **Certificate** menu -> **Add Custom Certificates…** -> select the **Root Certificate** tab
2. Click the **Import** button -> **Import P12...**
3. Select the **root-ca.p12** file and enter the password.
4. Trust your custom certificate in the Keychain Access app:

* Open the Keychain Access app
* Search for the certificate you've added. The name might be the common name (CN) of the certificate
* Double-click it to open it, then select **Always Trust**
* Close the window to save the change

![macOS Keychain Access certificate window with Trust set to Always Trust](<../.gitbook/assets/Screen Shot 2020-09-09 at 06.30.51.png>)

5\. Check that you see the green check mark, which means the certificate is installed and trusted.

![Proxyman Custom Certificates window showing the custom root certificate as Installed & Trusted](<../.gitbook/assets/Screen Shot 2020-09-09 at 20.52.39.png>)

## 8. Import as a Server/Client Certificate

For custom Server or Client certificates, don't generate a self-signed certificate. Ask your teammate or team lead for the certificate your company uses. It can be in DER/PEM or P12 format.

Then import it in the **Server Certificates** or **Client Certificates** tab of the Custom Certificates window.

![Proxyman Certificate Importer sheet with a PEM certificate file and a private key file selected](<../.gitbook/assets/Screen Shot 2020-06-26 at 10.54.35.png>)

{% hint style="info" %}
You don't need to trust the certificate in the System Keychain because it's not a Root Certificate.
{% endhint %}

## Learn more

* [How to generate and use Custom Root Certificates on Proxyman](https://proxyman.com/posts/2020-09-09-Generate-Self-Signed-Certificate-iOS13-Mac-Catalina)
