---
description: "Capture HTTP/HTTPS traffic from Docker services and configure containers to route outgoing requests through Proxyman."
---

# Docker

## 1. Capture traffic from your Docker Container

By default, Proxyman can capture the requests that you send from your Mac to a service running in a Docker container.

For example, here is a sample Docker container:

1. Set up a simple HTTP server with NodeJS + Express, then Dockerize it. You can find a guide at [https://nodejs.org/en/docs/guides/nodejs-docker-webapp/](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/)
2. Make sure you expose your server on port 8080.
3. You can verify it by opening http://localhost:8080 in Safari.

## 2. Capture traffic inside Docker Containers

Read the steps in [GitHub issue #419](https://github.com/ProxymanApp/Proxyman/issues/419#issuecomment-1059096490).

## 3. Alternative Solution:

1. Add docker-compose.proxyman.yml. Replace \<php8.1-fpm-xdebug> with your service

```yaml
version: '2'
services:
  php8.1-fpm-xdebug:
    environment:
      HTTP_PROXY: host.docker.internal:9090
      HTTPS_PROXY: host.docker.internal:9090
      http_proxy: host.docker.internal:9090
      https_proxy: host.docker.internal:9090
```

2. Start Docker:

`docker-compose -f docker-compose.yml -f docker-compose.proxyman.yml up -d`

Ref: [https://github.com/ProxymanApp/Proxyman/issues/1712#issuecomment-1642279537](https://github.com/ProxymanApp/Proxyman/issues/1712#issuecomment-1642279537)
