---
description: Capture HTTP/HTTPS traffic from Python with Proxyman
---

# Python

## 1. New Automatic Solution (v4.7.0 or later) ✅

Proxyman v4.7.0 or later can capture HTTP/HTTPS traffic from Python with 1-click.

* 1-click solution: No need to manually set HTTP Proxy config or trust the self-signed certificate.
* Support many Python libraries: request, http.client, urllib3, httpx and aiohttp

### How to use:

1. Open Proxyman -> Setup Menu -> Automatic Setup
2. Click on "Open New Terminal"
3. Accept the Apple Script permission prompt if needed
4. The New Terminal app is launched -> You can start your Python Backend Server, or Run scripts => Proxyman automatically captures all traffic.
5. Done ✅

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.18.19@2x.jpg" alt=""><figcaption><p>Capture NodeJS Traffic with Proxyman</p></figcaption></figure>

Please check out the Automatic Setup page:

{% content-ref url="../automatic-setup/automatic-setup.md" %}
[automatic-setup.md](../automatic-setup/automatic-setup.md)
{% endcontent-ref %}

##

## 2. Old Solution (Not recommended) ❌

### 1. Script Approach

1. Use [the following script ](https://github.com/ProxymanApp/Proxyman/issues/1220#issuecomment-1249090359)to automatically install/remove the certificate to Python.
2. Save the script to \~/desktop file with the name is `script.py`&#x20;

* Add Certificate:&#x20;

```bash
$ python3 script.py add
```

* Remove Certificate

```
$ python3 script.py remove
```

{% hint style="info" %}
For macOS 12.2 or later, make sure you use `python3`

Credit to [@novitae](https://github.com/novitae)
{% endhint %}

### 2. Manual Approach

### - Install Proxyman on the Python environment

By default, Python on macOS doesn't trust Proxyman self-signed certificates. As a result, you might encounter SSL Error if you try to intercept HTTPS traffic.&#x20;

If you would like to intercept HTTPS Traffic from your Python script, you have to explicitly **tell Python to use the Proxyman Root Certificate** at `~/.proxyman/proxyman-ca.pem`

Please follow the guideline:

1. Install Proxyman Certificate on Mac (If you've done it, please skip it. If not, please check out [MacOS Guideline](macos.md#install-certificates-on-macos)).
2. Run the following CLI on your Terminal app

```bash
$ export SSL_CERT_FILE=~/.proxyman/proxyman-ca.pem
$ export REQUESTS_CA_BUNDLE=~/.proxyman/proxyman-ca.pem
$ echo "export REQUESTS_CA_BUNDLE=~/.proxyman/proxyman-ca.pem" >> ~/.bash_profile ; source ~/.bash_profile
```

3\. Done.

### - Revert the change

If you don't use Proxyman, please revert the change by commenting out:

```bash
# export REQUESTS_CA_BUNDLE=~/.proxyman/proxyman-ca.pem
```

in \~/.bash\_profile

## 3. Troubleshooting

#### 3.1 Proxyman could not capture HTTP traffic from my Python code.

**Solution**: Please use the [Automatic Setup](../automatic-setup/automatic-setup.md).

### Reference

* [https://github.com/ProxymanApp/Proxyman/issues/948#issuecomment-890520435](https://github.com/ProxymanApp/Proxyman/issues/948#issuecomment-890520435)
* [https://github.com/ProxymanApp/Proxyman/issues/1220](https://github.com/ProxymanApp/Proxyman/issues/1220)
