# Charles Proxy Converter

### 1. What's it?

Proxyman is capable of converting and reading the `chls` files from Charles Proxy app to `har` format that Proxyman can understand.

{% hint style="info" %}
It requires that Charles Proxy is already installed in order to convert `chls` files&#x20;
{% endhint %}

You can manually convert the files from File menu -> Convert -> `chls` to `har`

![](<../.gitbook/assets/Screen Shot 2020-05-03 at 18.31.39.png>)

### 2. How it works?

In general, Proxyman use [Convert CLI from Charles Proxy](https://www.charlesproxy.com/documentation/tools/command-line-tools/) to convert .chls to .har, which Proxyman can understand.

1.  As soon as you open `chls` file, Proxyman tries to find Charles Proxy app, which has bundle ID is&#x20;

    `com.xk72.Charles`
2. Convert by using convert command

```
$ ./Applications/Charles.app/Contents/MacOS/Charles convert ~/Desktop/input.chls ~/Desktop/output.har

```

3\. The output is `har` format in your Desktop directory

### 3. How to use?

There are several ways to open `chls` files:

* Open the `chls` file directly (Double-Click on the file, or Open With from Finder app)
* Drag and drop the file to Proxyman app
* File -> Open and select `chls` files
