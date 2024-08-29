# Docker

### 1. Capture traffic from your Docker Container

By default, Proxyman can capture all traffic that you access from your Docker Container if you access it from your Mac Devices.

To elaborate, here is the sample Docker Container:

1. Set up a simple HTTP Server by NodeJS + Express. Then Dockerizing it. You can find it at [https://nodejs.org/en/docs/guides/nodejs-docker-webapp/](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/)
2. Makes sure we expose your server via port 8080.
3. You can verify it by opening http://localhost:8080 on Safari.

### 2. Capture traffic inside Docker Containers

Read more at [https://github.com/ProxymanApp/Proxyman/issues/419#issuecomment-1059096490](https://github.com/ProxymanApp/Proxyman/issues/419#issuecomment-1059096490)

### 3. Alternative Solution:

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

2. Start the Docker:

`docker-compose -f docker-compose.yml -f docker-compose.proxyman.yml up -d`

Ref: [https://github.com/ProxymanApp/Proxyman/issues/1712#issuecomment-1642279537](https://github.com/ProxymanApp/Proxyman/issues/1712#issuecomment-1642279537)
