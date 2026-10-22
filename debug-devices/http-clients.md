---
description: "Configure Postman, Insomnia, and Paw to send HTTP/HTTPS traffic through Proxyman and troubleshoot certificate errors."
---

# HTTP Clients

## 1. Problems

Proxyman might not capture requests, or you might get an SSL error, when you send HTTP/HTTPS requests from some HTTP clients, such as [Postman](https://www.postman.com/), [Insomnia Rest](https://insomnia.rest/), and [Paw](https://paw.cloud/).

This page shows how to make them work with Proxyman.

## 2. Postman

1. Open Postman Settings
2. In the General tab -> Uncheck the "SSL certificate verification" checkbox
3. In the Proxy tab -> Check "Use the system proxy" and "Respect `HTTP_PROXY`, `HTTPS_PROXY`, and `NO_PROXY` environment variables".

![Postman Settings, Proxy tab, with Use the system proxy checked](../.gitbook/assets/Postman\_And\_Proxyman.jpg)

## 3. Insomnia Rest

1. Open Insomnia Preferences -> General tab
2. Uncheck the "Validate certificates" checkbox
3. Check "Enable proxy" and enter `localhost:9090` in the HTTP Proxy and HTTPS Proxy text boxes.

![Insomnia Preferences with Validate certificates unchecked and the proxy set to localhost:9090](../.gitbook/assets/Insomnia\_And\_Proxyman.jpg)

## 4. Paw

By default, the Paw app uses the system proxy configuration, so Proxyman works out of the box.

If you don't see any Paw traffic in Proxyman, please double-check:

1. Open Paw Preferences.
2. In the Network tab, make sure Proxy is set to System Proxy Configuration.

![Paw Preferences, Network tab, with Proxy set to System Proxy Configuration](../.gitbook/assets/Paw\_Proxyman.jpg)
