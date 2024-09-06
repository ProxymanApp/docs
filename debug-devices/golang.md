# Golang

## 1. Problems

* Proxyman can't capture any HTTP/HTTPS traffic from the Golang Server.
* The reason is that some network libraries (such as net/http) won't respect the System HTTP Proxy, so no traffic goes through the Proxyman app.

## 2. Solution

### net/http

1. Config Proxy to Proxyman, by default, it's at IP = localhost, port 9090
2. Tell the Transport to trust Proxyman self-signed certificate. Otherwise, you will get an SSL Error because net/http rejects.

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
