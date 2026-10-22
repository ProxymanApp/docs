---
description: >-
  Filter JSON responses in Proxyman with text search, regex, JSONPath and jq,
  or show only the keys and values that match in the Treeview tab.
---

# Filter JSON Response

You can quickly filter a JSON response in these ways:

## 1. Filter on JSON Previewer

* Press **⌘F** in the Body tab to search
* Supports Regex
* Jump to the next match

## 2. JSONPath

Proxyman supports [JSONPath](https://github.com/json-path/JsonPath#path-examples) to quickly query data in a JSON document.

<figure><img src="../.gitbook/assets/proxyman-treeview-jsonpath-filter.jpg" alt="Proxyman Treeview tab with the JSON Path $.slideshow.slides[*].title returning two slide titles"><figcaption><p>Filter JSON with JSON Path</p></figcaption></figure>

Read the JSONPath page to learn the syntax.

{% content-ref url="jsonpaths.md" %}
[jsonpaths.md](jsonpaths.md)
{% endcontent-ref %}

You can also filter JSON with jq. Read the [jq](jq.md) page.

## 3. Search in the Treeview

* Press **⌘F** in the Treeview tab and choose a mode: Search, Filter, JSON Path, or jq.
* **Search** highlights the keys and values that contain the search text.

## 4. Filter by Keys or Values

* **Filter** shows only the nodes whose key or value contains the search text.

<figure><img src="../.gitbook/assets/proxyman-treeview-filter-mode.jpg" alt="Proxyman Treeview filter mode menu with Search, Filter, JSON Path and jq options"><figcaption><p>Pick a filter mode</p></figcaption></figure>
