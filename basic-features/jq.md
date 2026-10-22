---
description: >-
  Filter and transform JSON request and response bodies in Proxyman with jq in
  the JSON and Treeview tabs. Learn how to open the JSON tab and use jq.
---

# JQ

## 1. What's it?

* jq is a small language for JSON data. It works like sed does for text: you can slice, filter, map, and transform JSON data.
* Available on Proxyman 5.24.0 or later

{% hint style="success" %}
- You can use the jq filter in the JSON tab and the Treeview tab. To add the JSON tab, click the + button on the Request or Response toolbar and select JSON.
{% endhint %}

<div align="center" data-full-width="false"><figure><img src="../.gitbook/assets/481323588-7ae7cb0a-ca66-4199-a16d-e171960a9814.jpg" alt="Proxyman JSON tab with the jq filter mode and the .json[] expression applied to a response"><figcaption></figcaption></figure></div>

## 2. Syntax

* Read the [jq manual](https://jqlang.org/manual/#basic-filters) to learn how to write jq filters.
* You can also use jq to create a [custom column](custom-header-column.md) from a JSON body.
