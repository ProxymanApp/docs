---
description: Capture HTTP/2 traffic in Proxyman for macOS and inspect requests, responses, trailers, and negotiated protocols.
---

# HTTP/2

## 1. What's it?

HTTP/2 lets several requests share one connection at the same time. Proxyman captures each request and response as a separate exchange, so you can inspect them with the usual previewers and debugging tools.

{% hint style="info" %}
HTTP/2 is available in the regular Proxyman macOS release from v26.0.0. It is off by default. A separate beta app is no longer needed.
{% endhint %}

## 2. Benefits

* Inspect HTTP/2 requests and responses from apps and browsers that use Proxyman.
* Follow concurrent requests on a shared connection.
* Read headers, bodies, and trailer headers sent after a body.
* Check the HTTP version used by a captured request.
* Inspect the upstream protocol in [Connection Log](connection-log.md), when recorded.

HTTP/2 uses header compression and connection reuse to reduce overhead. Results depend on the app, server, and network. Enabling it does not make every request faster.

## 3. How to enable it?

1. Open Proxyman v26.0.0 or later on your Mac.
2. Go to **Proxyman → Settings → General**.
3. In the **Proxy** section, turn on **Use HTTP/2**.
4. For HTTPS content, install and trust the Proxyman certificate on the client device.
5. Enable [SSL Proxying](ssl-proxying.md) for the app or domain.
6. Send a fresh request or reload the page.

<!-- IMAGE PLACEHOLDER: Settings > General > Proxy with Use HTTP/2 enabled. -->

{% hint style="warning" %}
Changing this setting closes existing connections. Send fresh requests afterward. Active WebSocket and Server-Sent Events connections may also need to reconnect.
{% endhint %}

For certificate setup, see the [macOS guide](../debug-devices/macos.md). A remote device must trust the certificate and send its traffic through Proxyman on your Mac. See the [iOS](../debug-devices/ios-device.md) or [Android](../debug-devices/android-device/README.md) setup guide.

To turn HTTP/2 off, uncheck **Use HTTP/2** in the same Settings section.

## 4. What does it capture?

Select a request in the main list to inspect the available details:

* Request method, URL, query parameters, cookies, and headers.
* Request and response bodies, such as JSON, form data, text, or binary content.
* Response status and headers.
* Request and response trailers, when present.
* Timing and HTTP version information.
* Recorded connection details, including upstream protocol negotiation.

Trailers are headers sent after the body. For gRPC traffic, check `grpc-status` and `grpc-message` in the headers or trailers. HTTP 200 alone does not prove the RPC succeeded. Binary payloads may need further decoding.

<!-- IMAGE PLACEHOLDER: An HTTP/2 exchange showing the request version and response trailer headers. -->

## 5. How to check the protocol?

The setting allows HTTP/2 with HTTP/1.1 fallback. It does not guarantee that every request uses HTTP/2.

There are two connections:

* The client connection, from your app or browser to Proxyman.
* The upstream connection, from Proxyman to the server.

These connections can use different HTTP versions. Check the request's HTTP version for the client connection. Open **Connection Log** in the Request panel to inspect the upstream protocol, when recorded.

* `h2` means HTTP/2.
* `http/1.1` means HTTP/1.1.
* An offered protocol is not proof that the server selected it. Check the accepted protocol.
* Older saved captures may lack upstream protocol details. Missing data does not mean HTTP/1.1.

<!-- IMAGE PLACEHOLDER: Connection Log showing the protocol accepted by the upstream server. -->

## 6. Connection info in Connection Log

* Select a request, then open **Connection Log** in the Request panel, next to **Summary**.
* Read a log similar to `curl -v`, with DNS results, connection attempts, TLS and certificate details, and HTTP headers.
* Check `ALPN: server accepted h2` to confirm the upstream connection uses HTTP/2. Reused connections are marked with `Re-using existing connection`.
* `*` marks connection events, `>` marks the request, and `<` marks the response.

Example excerpt with sample values:

```text
* Host api.example.com:443 was resolved.
* IPv4: 192.0.2.10
* Connected to api.example.com (192.0.2.10) port 443
* ALPN: Proxyman offers h2,http/1.1
* SSL connection using TLSv1.3 / TLS_AES_128_GCM_SHA256
* ALPN: server accepted h2
* using HTTP/2
> GET /profile HTTP/2
< HTTP/2 200 OK
* Connection #0 to host api.example.com left intact
```

If the tab is hidden, enable **Connection Log** under Request in [Custom Previewer Tab](custom-previewer-tab.md). See the [Connection Log guide](connection-log.md) for all fields.

<!-- IMAGE PLACEHOLDER: Connection Log in the Request panel showing an HTTP/2 connection. -->

## 7. Troubleshooting

If a request still uses HTTP/1.1:

* Check **Use HTTP/2**, then send a fresh request.
* Confirm the client supports and negotiates HTTP/2.
* Check whether the upstream server supports HTTP/2. Fallback may be expected.
* Inspect both connections before deciding which side used HTTP/1.1.

If HTTPS content is missing:

* Check that the client sends its traffic through Proxyman.
* Check certificate trust and the domain's SSL Proxying rule.
* If the client rejects the certificate, see [SSL errors](../troubleshooting/get-ssl-error-from-https-request-and-response.md).

## 8. Related guides

* [SSL Proxying](ssl-proxying.md)
* [Connection Log](connection-log.md)
* [Split View](split-view.md)
* [Tab View](multiple-tabs.md)
* [Upstream ALPN and HTTP/2 Scripting settings](../scripting/snippet-code.md#upstream-alpn-and-http2-settings)
* [HTTP/2 release blog](https://proxyman.com/posts/2026-09-19-http2-is-finally-here)
