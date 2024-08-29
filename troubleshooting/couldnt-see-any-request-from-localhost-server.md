# I could not see any requests from my localhost server

## 1. Problem: I develop a local NodeJS, Ruby, or Python Backend at **http://localhost:3000**, but when I visit **http://localhost:3000** from Google Chrome, Safari  -> There is no traffic on the Proxyman app.

**Why does this happen?** By default, on macOS, all localhost requests don't go through the System HTTP Proxy. Therefore, there is no traffic recorded by Proxyman app.

### 2. Solution

There are two solutions to fix it: You should follow either one of the following solutions.

### Solution 1: Map **localhost** to the domain name in `/etc/hosts` (recommended ✅)

1. Open `etc/hosts` file with Vim or VS Code.

```
$ sudo vim /etc/hosts
```

2\. Add Domain Name with both **IPv4** and **IPv6** (You can change the `proxyman.debug` with your name)

```
127.0.0.1 proxyman.debug
::1 proxyman.debug
```

<figure><img src="../.gitbook/assets/Screenshot 2023-09-01 at 22.11.30.png" alt=""><figcaption><p>Add proxyman.debug in /etc/host</p></figcaption></figure>

3\. Save the file with `sudo` permission

4\. Access your localhost server by **http://proxyman.debug:3000** (replace 3000 with your localhost ports)&#x20;

6\. Enjoy debugging!

![](<../.gitbook/assets/Screen Shot 2020-04-25 at 16.55.18.png>)

{% hint style="info" %}
If you use a `local` as a suffix, e.g. proxyman.local, make sure to remove the \`\*.local\` from the Bypass Proxy List ([Instruction](https://docs.proxyman.io/troubleshooting/.local-doesnt-appear-in-proxyman#2-solution)).
{% endhint %}

###

### Solution 2: Use **localhost.proxyman.io** instead of **localhost**

Proxyman uses Cloudflare and sets the DNS of **localhost.proxyman.io** to 127.0.0.1 (localhost). As a result, Proxyman can capture the local traffic as usual ✅&#x20;

For example:

<table data-header-hidden><thead><tr><th width="374">Old URL</th><th>New URL</th></tr></thead><tbody><tr><td>Old URL</td><td>New URL</td></tr><tr><td>localhost:3000</td><td>localhost.proxyman.io:3000</td></tr><tr><td>localhost:8080</td><td>localhost.proxyman.io:8080</td></tr><tr><td>...</td><td>...</td></tr></tbody></table>
