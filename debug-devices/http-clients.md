# HTTP Clients

### 1. Problems

Proxyman might not capture or get SSL Error from HTTP/HTTPS Requests, which makes from some HTTP Clients, such as [Postman](https://www.postman.com/), [Insomnia Rest](https://insomnia.rest/), and [Paw](https://paw.cloud/) app.

This documentation would provide a solution to make Proxyman works.

### 2. Postman

1. Open Postman Preference
2. In General Tab -> Uncheck the "SSL certificate validation" checkbox
3. In Proxy Tab -> Check the "Use the System Proxy" and "Respect `HTTP_PROXY` _and `HTTPS_PROXY`_ variables".

![Config to make Postman works with Proxyman](../.gitbook/assets/Postman\_And\_Proxyman.jpg)

### 3. Insomnia Rest

1. Open Insomnia Preference -> General Tab
2. Uncheck the "Validate Certificates" checkbox
3. Check "Enable Proxy" and enter `localhost:9090` in HTTP Proxy and HTTPS Proxy Textbox.

![Config to make Insomnia Rest works with Proxyman](../.gitbook/assets/Insomnia\_And\_Proxyman.jpg)

### 4. Paw

By default, Paw app uses the System Proxy Configuration. Thus, Proxyman can work out of the box.

If you don't see any Paw traffic from Proxyman, please double-check:

1. Open Paw Preference.
2. Make sure you're using System Proxy Configuration in the Proxy Setting.

![Paw and Proxyman](../.gitbook/assets/Paw\_Proxyman.jpg)
