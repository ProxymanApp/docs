---
description: "Use Proxyman Map Local Directory to serve matching requests from files in a local folder, and fall back to the server when a file is missing."
---

# Map Local (Directory)

## 1. What's it?

It's a handy tool to map matched requests to local files in a selected directory. If a local file doesn't exist, Proxyman serves the response from the real server.

If you would like to map a single local file, check out the Map Local (File) page.

{% content-ref url="map-local.md" %}
[map-local.md](map-local.md)
{% endcontent-ref %}

## 2. How to use

### 2.1 Map a path and its subdirectories

`api.proxyman.io/build/v1/*` => All sub-paths after `/v1/` will map to a selected directory.

For instance, we select `~/desktop/my_folder` as the local directory.

| Real URL                                   | Resolved Local Path              |
| ------------------------------------------ | -------------------------------- |
| http://api.proxyman.io/build/v1/index.html | \~/desktop/my\_folder/index.html |
| http://api.proxyman.io/build/v1/js/main.js | \~/desktop/my\_folder/js/main.js |

#### How to config

| Rule     | How to use                                                                                     | Examples                                                                                                            |
| -------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Wildcard | <ul><li>Check the "Include all subpaths of this URL" checkbox</li><li>Or use /* at the end of the URL</li></ul> | <ul><li>api.proxyman.io/build/v1/ (Check ON)</li><li>api.proxyman.io/build/v1/*</li></ul>                           |
| Regex    | <ul><li>Use (.*) at the end</li></ul>                                                          | <ul><li>https:\/\/api.proxyman.io\/build\/v1\/(.*)</li><li>https:\/\/api.proxyman.io\/build\/v1\/(.*.css)</li></ul> |

{% hint style="info" %}
Make sure you use the `()` Regex group operator to tell Proxyman where to map.&#x20;
{% endhint %}

### 2.2 Map Entire Host

`api.proxyman.io/*` => All sub-paths will map to a selected directory.

For instance, we select `~/desktop/my_folder` as the local directory.

| Real URL                                   | Resolved Local Path                       |
| ------------------------------------------ | ----------------------------------------- |
| http://api.proxyman.io/build/v1/index.html | \~/desktop/my\_folder/build/v1/index.html |
| http://api.proxyman.io/build/v1/js/main.js | \~/desktop/my\_folder/build/v1/js/main.js |

#### How to config

| Rule     | How to use                                                      | Examples                                                                                      |
| -------- | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Wildcard | <ul><li>Leave the path blank</li></ul>                          | <ul><li>api.proxyman.io</li></ul>                                                             |
| Regex    | <ul><li>Use single path that contains (.*) at the end</li></ul> | <ul><li>https:\/\/api.proxyman.io\/(.*)</li><li>https:\/\/api.proxyman.io\/(*.html)</li></ul> |

## 3. Map Local Directory with Scripting Tool ✅&#x20;

If you would like to do Map Local Directory with **complicated rules,** check out [Scripting](../scripting/script.md#1-whats-it), since it's easier to get the same result.

Please check out our [Snippet Code](../scripting/snippet-code.md#2-common-on-request-and-response) to see how to map a local file with JavaScript code.
