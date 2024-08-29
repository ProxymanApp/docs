# Rust

## 1. Problem

Proxyman can't automatically capture HTTP/HTTPS traffic which is called from `reqwest` in Rust because of:

* `reqwest` doesn't respect the system HTTP Proxy -> No traffic goes through Proxyman
* `reqwest` doesn't trust any self-signed Proxyman Certificate -> Get SSL Error

## 2. Solution

* Manually set the Proxy to Proxyman at `http://localhost:9090`
* Disable SSL Verification

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
