---
description: Capture HTTP/HTTPS traffic from NodeJS with Proxyman
---

# NodeJS

## 1. New Automatic Solution (v4.7.0 or later) ✅

Proxyman v4.7.0 or later can capture HTTP/HTTPS traffic from NodeJS with 1-click.

* 1-click solution: No need to manually set HTTP Proxy config or trust the self-signed certificate.
* Support many NodeJS libraries: axios, got, superagent, fetch, and node-fetch

### How to use:

1. Open Proxyman -> Setup Menu -> Automatic Setup
2. Click on "Open New Terminal"
3. Accept the Apple Script permission prompt if needed
4. The New Terminal app is launched -> You can start your NodeJS Backend Server, or Run scripts => Proxyman automatically captures all traffic.
5. For example:&#x20;

```
$ npm start
```

Done ✅

<figure><img src="../.gitbook/assets/CleanShot 2023-04-22 at 15.18.19@2x.jpg" alt=""><figcaption><p>Capture NodeJS Traffic</p></figcaption></figure>

Please check out the Automatic Setup page:

{% content-ref url="../automatic-setup/automatic-setup.md" %}
[automatic-setup.md](../automatic-setup/automatic-setup.md)
{% endcontent-ref %}

## 2. Old Solution (Not recommended) ❌

There are common problems when using NodeJS + Proxyman:

### 1. Proxyman could not capture http://localhost:3000 requests to my NodeJS Server

If you're using NodeJS to serve a localhost website (e.g http://localhost:3000), Proxyman might not work. For example: Use ExpressJS to serve an API Server at http://localhost:3000

### Solution:

Please check out this solution.

### 2. Proxyman could not capture HTTP requests, which are called from my NodeJS local server.

* I use [fetch](https://www.npmjs.com/package/node-fetch) or [axios](https://github.com/axios/axios) doesn't show on the Proxyman app
* Get SSL Error from HTTPS Requests

### Solution

By default, all HTTP/HTTPS requests which are called from your NodeJS library don't go through HTTP Proxy Server. Thus, Proxyman could not capture the traffic.

### 1. node-fetch

1. Install [global-agent](https://github.com/gajus/global-agent) package

```bash
npm install global-agent
```

2\. At the top of your NodeJS code, add the following code:

```javascript
import { bootstrap } from 'global-agent';
bootstrap();
process.env['NODE_TLS_REJECT_UNAUTHORIZED'] = '0';
```

3\. Add this env to your current bash. Make sure Proxyman is listening at port 9090

```
export GLOBAL_AGENT_HTTP_PROXY=http://127.0.0.1:9090
```

4\. Done ✅&#x20;

Run your NodeJS Script again and the HTTP/HTTPS request would appear on the Proxyman app.

#### Sample code

```javascript
import fetch from 'node-fetch';

// Setup global-agent
import { bootstrap } from 'global-agent';
bootstrap();
process.env['NODE_TLS_REJECT_UNAUTHORIZED'] = '0';

// fetch the data
const response = await fetch('https://httpbin.org/get?id=123');
const data = await response.json();

// Done
console.log(data);
```

### 2. Axios

According to Axios Documentation, we can simply provide the HTTP\_PROXY and HTTPS\_PROXY environment.

1. Click on the Proxyman Status Menu
2. Copy Shell Command

<figure><img src="../.gitbook/assets/Screenshot 2023-04-15 at 10.39.02.jpg" alt=""><figcaption></figcaption></figure>

3. Open the Terminal and run the paste content: For example export https\_proxy=http://192.168.1.103:9090 http\_proxy=http://192.168.1.103:9090
4. On the same Terminal -> Start your NodeJS Server with axios.
5. Axios will proxy the traffic to Proxyman.
6. Done ✅

### 3. I use different NodeJS Library

If you're not using fetch or axios, the configuration might be different. Please check out your lib Document to see how to set the proxy and trust the Proxyman certificate.

* Discussion at [https://github.com/ProxymanApp/Proxyman/issues/236](https://github.com/ProxymanApp/Proxyman/issues/236)
