# Custom Certificates

### 1. What's it?

Proxyman supports Custom **Root Certificate**, **Server Certificates, and** **Client Certificates** that allow you to add your certificate that Proxyman uses to establish the SSL-Connection between your clients, servers, and Proxyman app.

| Custom Certificate Type | Purpose                                                                                           | How Proxyman uses                                         |
| ----------------------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| **Server Certificate**  | For intercepting HTTPS Traffic from clients that use SSL-Pinning                                 | Use this certificate for SSL-Handshake to your Clients    |
| **Client Certificate**  | For intercepting HTTPS Traffic from clients that use Mutual Authentication                        | Use this certificate for SSL-Handshake to specific Server |
| **Root Certificate**    | For intercepting HTTPS Traffic from clients and servers without using local Proxyman certificates | SSL Handshake for both clients & servers                  |

![](<../.gitbook/assets/Screen Shot 2020-09-09 at 15.52.42 (1).png>)

{% hint style="info" %}
Even though the Proxyman Root Certificate is locally generated in your machine, you can manually generate and add to Proxyman. [Read more](custom-certificates.md#6-how-to-generate-self-signed-certificates-that-meet-apples-requirements)
{% endhint %}

### 2. Certificate Formats

Proxyman accepts the following formats:

| Custom Certificate  | PEM or DER    | PKCS #12 (p12) |
| ------------------- | ------------- | -------------- |
| Root Certificate    | Not Supported | Supported      |
| Client Certificate  | Supported     | Supported      |
| Server Certificate  | Supported     | Supported      |

* PKCS #12 (p12).
* PEM or DER Private Key and Certificate file.

{% hint style="info" %}
* Proxyman automatically determines the format of the Private Key and Certificate file (Support PEM or DER).
* Proxyman will prompt to enter the password if import an encrypted Private Key or PKCS #12 file.
* All passphrases are securely stored in Proxyman Keychain.
{% endhint %}

{% hint style="info" %}
If your certificates are in different formats that Proxyman supports, please convert them to p12 or PEM/DER format before importing.
{% endhint %}

### 3. Certificate Requirement on macOS 10.15+ and iOS 13+

If you're using a custom Root Certificate or Server Certificate on macOS 10.15 or iOS 13, you might encounter the failed handshake on Safari or iOS devices if the following requirements don't meet:

* RSA Key must have a key size is greater than 2048 bits
* The hash algorithm is SHA-2 family
* DNS Name of the server must be present on Subject Alternative Name. Common Name is no longer trusted
* Valid certificate (Current day is in Not Before and Not After)
* TLS server certificates must contain an ExtendedKeyUsage (EKU) extension containing the **id-kp-serverAuth** OID.

Read more [https://support.apple.com/en-us/HT210176](https://support.apple.com/en-us/HT210176)

{% hint style="info" %}
If it's too complicated for you, we recommend letting Proxyman performs it automatically. Please visit Certificate Menu -> Install Certificate on this Mac -> Select **Automatic** Tab.
{% endhint %}

### 4. Common issues

| Problem                                                | Solution                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Private Key and Certificate are not matched            | Try different certificates and private keys and make sure they are matched                                                                                                                                                                                                                               |
| Get SSL Handshake Error for custom certificates        | <ul><li>Try to add the custom Certificate to System Keychain and Trust it</li><li>Certificate doesn't match the requirement from macOS => Read <a href="custom-certificates.md#3-certificate-requirement-on-macos-10-15-and-ios-13">section 3</a></li><li>Check expires day of the Certificate</li></ul> |
| Could not import certificate due to invalid passphrase | Ask your leader to give the correct passphrase to open the encrypted Private Key or P12 file                                                                                                                                                                                                             |

### 5. How to use

* Access from **Certificate Menu** -> **Add Custom Certificate**

![](<../.gitbook/assets/Screen Shot 2021-07-31 at 20.21.35.png>)

### **6. How to generate self-signed certificates for Custom Root Certificate that comply with new Apple's Security Requirements**

Due to [Apple's requirements from iOS 13 and Catalina (10.15)](custom-certificates.md#3-certificate-requirement-on-macos-10-15-and-ios-13), It requires extra configuration to generate the self-signed certificate properly.

The following steps will guide you on how to do it properly:

1. Prepare a `cert.config` file on the **Desktop folder**

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

* Please update values for C, L, O, CN, and OU parameters.

2\. Generate RSA Key in the Terminal app. (Replace **your\_password** with any password, e.g. 123456)

```bash
cd ~/Desktop
openssl genrsa -aes256 -passout pass:your_password -out key.pem 2048
```

&#x20;3\. Generate the self-signed certificate and private key. (Replace **your\_password** with the password in step 2)

```
openssl req -x509 -new -nodes -passin pass:your_password -config cert.config -key key.pem -sha256 -extensions v3_ca -days 825 -out root-ca.pem
```

4\. Convert to p12 format. (Replace **your\_password** with the password in step 2)

```
openssl pkcs12 -export -legacy -out root-ca.p12 -in root-ca.pem -inkey key.pem -passin pass:your_password -passout pass:your_password
```

5\. Finally, you would have **root-ca.p12** file and move to the next step



{% hint style="info" %}
If you can't import your custom certificate on macOS 14 (OpenSSL v3) or later, you should use the \`-legacy\` flag in step 4.

Ref: [https://stackoverflow.com/questions/70431528/mac-verification-failed-during-pkcs12-import-wrong-password-azure-devops](https://stackoverflow.com/questions/70431528/mac-verification-failed-during-pkcs12-import-wrong-password-azure-devops)
{% endhint %}



### 7. Import as a Custom Root Certificate

1. Go to Certificate Menu -> Custom Certificate -> Select Root Certificate Tab
2. Click **Import** button -> P12
3. Select **root-ca.p12** file and enter the password.
4. Trust your custom certificate in Keychain Access App:

* Open Keychain Access App
* Search for the certificate you've added. The name might be the common name (CN) of the certificate
* Double Click to open and select Always Trust
* Click "X" and save the change

![](<../.gitbook/assets/Screen Shot 2020-09-09 at 06.30.51.png>)

5\. Please verify that you can see the Green Tick that shows the certificate is installed and trusted properly.

![Custom Root Certificate is installed and trusted properly. Ready to go!](<../.gitbook/assets/Screen Shot 2020-09-09 at 20.52.39.png>)

### 8. Import as a Server/Client Certificate

For custom Server/Client certificates, you should not generate a self-signed certificate. Please ask your workmate or team lead about the certificate that the company is using. It could be in DER/PEM or P12 format.

Then import the certificate as a Server / Client Certificate in Custom Certificate Window.

![Import PEM/DER key and private key to Custom Client/Server Certificate](<../.gitbook/assets/Screen Shot 2020-06-26 at 10.54.35.png>)

{% hint style="info" %}
You don't need to trust the certificate on System Keychain since it's not a Root Certificate.
{% endhint %}
