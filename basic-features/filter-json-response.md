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

![JSON response in the Body tab with a search for Friedland and two highlighted matches](../.gitbook/assets/Screen\_Shot\_2020-10-06\_at\_19\_47\_47.png)

## 2. JSONPath

Proxyman supports [JSONPath](https://github.com/json-path/JsonPath#path-examples) to quickly query data in a JSON document.

![Treeview tab filtering a JSON response with a JSONPath expression that returns all user names](../.gitbook/assets/Screen\_Shot\_2021-08-01\_at\_10\_29\_23.png)

Read the JSONPath page to learn the syntax.

{% content-ref url="jsonpaths.md" %}
[jsonpaths.md](jsonpaths.md)
{% endcontent-ref %}

You can also filter JSON with jq. Read the [jq](jq.md) page.

## 3. Search in the Treeview

* Press **⌘F** in the Treeview tab and choose a mode: Search, Filter, JSON Path, or jq.
* **Search** highlights the keys and values that contain the search text.

![Treeview tab of an older Proxyman version filtering a JSON response with a key path](../.gitbook/assets/Screen\_Shot\_2020-10-06\_at\_19\_30\_35.png)

## 4. Filter by Keys or Values

* **Filter** shows only the nodes whose key or value contains the search text.

![Treeview filter mode menu from an older Proxyman version with Key Paths, All Keys and All Values](<../.gitbook/assets/Screen Shot 2020-10-06 at 14.21.26.png>)
