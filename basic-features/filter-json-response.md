# Filter JSON Response

You can quickly filter the JSON Response with the following approach:

### 1. Filter on JSON Previewer

* **⌘F** to trigger the Filter
* Support Regex
* Support Jump Next

![](../.gitbook/assets/Screen\_Shot\_2020-10-06\_at\_19\_47\_47.png)

### 2. JSONPath

Proxyman supports [JSONPath](https://github.com/json-path/JsonPath#path-examples) for quickly querying the data in JSON Document.

![](../.gitbook/assets/Screen\_Shot\_2021-08-01\_at\_10\_29\_23.png)

Please check out JSONPath documentation.

{% content-ref url="jsonpaths.md" %}
[jsonpaths.md](jsonpaths.md)
{% endcontent-ref %}

### &#x20;3. KeyPaths

* Support Key Paths filter on JSON Tree View mode
* Search specifically the children keys&#x20;

Syntax example:

* **posts\[1].maker\[2]**: Go from Root -> Get item at index 1 of the Posts array -> Get the index 3 items of Makers array and filter out
* **users.name**: Get the name value of the "users" dictionary&#x20;

![](../.gitbook/assets/Screen\_Shot\_2020-10-06\_at\_19\_30\_35.png)

### 4. All Keys or All Values

* Show all nodes that the key or value contains the search text

![](<../.gitbook/assets/Screen Shot 2020-10-06 at 14.21.26.png>)
