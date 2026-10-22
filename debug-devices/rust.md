---
description: "Configure the proxy and certificate handling for Rust reqwest requests so their HTTP/HTTPS traffic appears in Proxyman."
---

# Rust

## 1. Problem

Proxyman can't automatically capture HTTP/HTTPS traffic from `reqwest` in Rust because:

* `reqwest` doesn't respect the system HTTP Proxy -> No traffic goes through Proxyman
* `reqwest` doesn't trust the self-signed Proxyman Certificate -> You get an SSL error

## 2. Solution

* Manually set the proxy to Proxyman at `http://localhost:9090`
* Disable SSL verification

```rust
use anyhow::Result;
use reqwest::Url;

#[tokio::main]
async fn main() -> Result<()> {
    let proxy_url = Url::parse("http://localhost:9090")?;
    let client = reqwest::Client::builder()
        .danger_accept_invalid_certs(true) // trust self-signed certificate
        .proxy(reqwest::Proxy::https(proxy_url)?) // Proxy to Proxyman
        .build()?;
    let response = client.get("https://httpbin.org/get").send().await?;

    if response.status().is_success() {
        let body = response.text().await?;
        println!("Response Text: {}", body);
    } else {
        println!("Request failed with status: {}", response.status());
    }

    Ok(())
}
```

{% hint style="info" %}
For apps that ignore the system proxy, you can also try [Network Extension](../advanced-features/network-extension.md) (Beta, macOS 26 or later). It captures traffic without setting a proxy in each app. For HTTPS, your Rust client still has to trust the Proxyman certificate, or skip verification as shown above.
{% endhint %}
