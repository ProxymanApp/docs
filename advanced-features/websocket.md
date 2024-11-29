---
description: Capture and debug Websocket from iOS devices / simulators with Proxyman
---

# WebSocket

## 1. What's it?

Proxyman could capture WebSocket (WS) and Secure WebSocket (WSS) traffic and easily preview it.

* Capture WS/WSS from iOS Physical devices and iOS Simulator (Required [Atlantis framework](https://github.com/ProxymanApp/atlantis))
* Capture WS/WSS from Web Browser and Mac applications.
* Capture WS/WSS from Android Physical devices or Android Emulators.
* Prettier WebSocket Message.
* Filter All / Sent / Received messages.
* See the content in JSON / Tree Preview / HEX format.
* Customize Columns: Frame, Length, Data, Time, ...&#x20;
* Auto decode Binary Message to JSON if possible
* Open WebSocket messages by external Editors, such as Sublime, VSCode

## 2. Capture WS/WSS from iOS

If your iOS app is using **URLSessionWebSocketTask** or iOS WebSocket libraries, e.g. Starscream, SocketRocket, etc. Proxyman might not be able to capture WS/WSS traffic.

* **Reason**: Apple's intention. **URLSessionWebSocketTask** doesn't respect the System HTTP Proxy. All WS/WSS traffic goes directly to the Internet. Thus, Proxyman or Charles Proxy can't capture it.
* Example Ap: [https://github.com/ProxymanApp/websocket-example-ios-app](https://github.com/ProxymanApp/websocket-example-ios-app)

### ✅ Solution 1 (Recommended for iOS 17 or later)

1. Follow the Setup guide for your [iOS Devices](../debug-devices/ios-device.md) or [iOS Simulators](../debug-devices/ios-simulator.md) (Make sure we installed and trusted the certificate on your device)
2. Proxyman Setup: Tools > Proxy Settings > SOCKS Proxy settings -> Enable it (Take note of the port)
3. On the main Proxyman app -> Take note of a current IP in the Proxyman Tools bar

<figure><img src="../.gitbook/assets/proxyman_capture_websocket_4.jpeg" alt=""><figcaption><p>Get Proxyman current IP</p></figcaption></figure>



4. On your app: Configure a SOCK Proxy in your App, make sure this is only available for debug builds by implementing a switch or something, you might not want your release build with this configuration.

* For NWConnection

{% code overflow="wrap" fullWidth="false" %}
```swift
let parameters = webSocketURL.scheme == "wss" ? NWParameters.tls : NWParameters.tcp

let options = NWProtocolWebSocket.Options()
options.autoReplyPing = true

parameters.defaultProtocolStack.applicationProtocols.insert(options, at: 0)

if #available(iOS 17.0, *) {
    let socksv5Proxy = NWEndpoint.hostPort(host: "x.x.x.x", port: 8889) //  Please x.x.x.x with a real Proxyman IP
    let config = ProxyConfiguration.init(socksv5Proxy: socksv5Proxy)
    let context = NWParameters.PrivacyContext(description: "my socksv5Proxy")
    context.proxyConfigurations = [config]

    parameters.setPrivacyContext(context)
}

let connection = NWConnection(to: .url(webSocketURL), using: parameters)
connection.start(queue: .main)
```
{% endcode %}

* For URLSession and URLSessionWebSocketTask

{% code overflow="wrap" fullWidth="false" %}
```swift
private lazy var urlSession: URLSession = {
    let config = URLSessionConfiguration.default
    if #available(iOS 17.0, *) {
        let socksv5Proxy = NWEndpoint.hostPort(host: "x.x.x.x", port: 8889) //  Please x.x.x.x with a real Proxyman IP
        let proxyConfig = ProxyConfiguration.init(socksv5Proxy: socksv5Proxy)
        config.proxyConfigurations = [proxyConfig]
    }

    return URLSession(configuration: config, delegate: nil, delegateQueue: nil)
}()
```
{% endcode %}

5. Done ✅

<figure><img src="../.gitbook/assets/Screenshot 2024-11-29 at 1.17.23 PM.jpg" alt=""><figcaption><p>Capture Websocket from iOS with Proxyman</p></figcaption></figure>

* Credit to [**FranklinSamboni**](https://github.com/FranklinSamboni) **->** [https://github.com/ProxymanApp/Proxyman/issues/586#issuecomment-2125082129](https://github.com/ProxymanApp/Proxyman/issues/586#issuecomment-2125082129)
* Tutorial: [https://proxyman.io/posts/2019-10-18-WebSocket-Debugging](https://proxyman.io/posts/2019-10-18-WebSocket-Debugging)

### ✅ Solution 2

Use [Atlantis Framework](https://github.com/ProxymanApp/atlantis#features) (developed by Proxyman) to capture WS/WSS **URLSessionWebSocketTask** traffic from iOS.

Read more at [https://github.com/ProxymanApp/atlantis](https://github.com/ProxymanApp/atlantis#wswss-traffic)

### Screenshots

![Capture Websocket](../.gitbook/assets/websocket.png)

## 3. Map Websocket from Localhost <-> Production

It's possible to map the WebSocket Traffic from localhost <-> Production. Please check out the [Map Remote Tool.](map-remote.md#7.4-map-websocket-from-localhost-to-production)

