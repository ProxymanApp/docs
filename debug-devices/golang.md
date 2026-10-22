---
description: >-
  Capture HTTP/HTTPS traffic from Go apps with Proxyman Automatic Setup. Works
  with net/http, fasthttp, resty, gorequest, req and grequests.
---

# Golang

## 1. New Automatic Solution (macOS v5.17.0 or later) ✅

Proxyman macOS v5.17.0 or later can capture HTTP/HTTPS traffic from Golang with 1 click.

* 1-click solution: No need to set the HTTP Proxy config or trust the self-signed certificate manually.
* ✅ Supports many Go network libraries: net/http, fasthttp, resty, gorequest, req, grequests

### How to use:

1. Open Proxyman -> Setup Menu -> Automatic Setup
2. Select your favorite Terminal -> Click the "Open New Terminal" button
3. Accept the AppleScript permission prompt if needed

<figure><img src="../.gitbook/assets/proxyman-automatic-setup-window.jpg" alt="Proxyman Automatic Setup window listing Golang libraries such as net/http and resty, with the Open New Terminal button"><figcaption><p>Open a pre-configured Terminal to intercept HTTPS from Go</p></figcaption></figure>

4. A new Terminal window opens -> Start your Golang backend server or run your scripts there => Proxyman captures all traffic automatically.
5. For example:&#x20;

```
$ go run main.go
```

6. Proxyman captures all HTTP/HTTPS traffic from Go, including net/http

<figure><img src="../.gitbook/assets/CleanShot 2025-03-18 at 09.56.44@2x.jpg" alt="Terminal running go run main.go next to Proxyman showing captured requests from net/http, fasthttp and resty"><figcaption><p>Capture and intercept HTTPS traffic from Go net/http</p></figcaption></figure>

* Go Example Code: [https://github.com/ProxymanApp/golang-example](https://github.com/ProxymanApp/golang-example)

## 2. Old Solution (Not recommended ❌)

* Proxyman can't capture any HTTP/HTTPS traffic from the Golang server.
* The reason is that some network libraries (such as net/http) don't respect the system HTTP Proxy, so no traffic goes through the Proxyman app.

### 2.1 Solution

#### net/http

1. Set the proxy to Proxyman. By default, it's at IP = localhost, port 9090
2. Tell the Transport to trust the Proxyman self-signed certificate. Otherwise, you get an SSL error because net/http rejects it.

```go
package main

import (
	"crypto/tls"
	"fmt"
	"io/ioutil"
	"log"
	"net/http"
	"net/url"
)

func main() {
	// Create a new HTTP client
	client := &http.Client{}

	// Configure the proxy
	proxyURL, err := url.Parse("http://localhost:9090")
	if err != nil {
		log.Fatal("Error parsing proxy URL:", err)
	}

	// Configure transport with proxy and TLS settings
	transport := &http.Transport{
		Proxy: http.ProxyURL(proxyURL),
		TLSClientConfig: &tls.Config{
			InsecureSkipVerify: true, // This allows self-signed certificates
		},
	}

	// Set the transport for the client
	client.Transport = transport

	// Make a request
	resp, err := client.Get("https://example.com")
	if err != nil {
		log.Fatal("Error making request:", err)
	}
	defer resp.Body.Close()

	// Read the response body
	body, err := ioutil.ReadAll(resp.Body)
	if err != nil {
		log.Fatal("Error reading response:", err)
	}

	// Print the response
	fmt.Printf("Status: %s\n", resp.Status)
	fmt.Printf("Body: %s\n", string(body))
}

```

## Learn more

* [Capture HTTP/HTTPS traffic from Golang with Proxyman](https://proxyman.com/golang) (Proxyman website)
