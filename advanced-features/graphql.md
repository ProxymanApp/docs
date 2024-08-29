# GraphQL

## 1. Use Debugging Tools with GraphQL Requests&#x20;

From Proxyman 2.27.0, we can use debugging tools with GraphQL Requests by specifying the GraphQL Query Name.

Matching by GraphQL QueryName works with Breakpoint, Map Local, Map Remote, Block List, Allow List, and the Scripting Tool.

#### How to use

1. Open the debugging tool (e.g. Breakpoint)
2. Create new Rule
3. Click on Use "Wildcard Dropdown" -> Advanced -> Check GraphQL QueryName.
4. Enter the GraphQL QueryName

By doing this way, the debugging tool will match the original matching rule firstly, then match the GraphQL QueryName.

![Enable GraphQL QueryName](../.gitbook/assets/Screen\_Shot\_2021-05-26\_at\_15\_46\_13.png)

![Specify the GraphQL QueryName](../.gitbook/assets/Screen\_Shot\_2021-05-26\_at\_15\_48\_17.png)

{% hint style="info" %}
From build 3.0.0, Proxyman automatically fills the GraphQL Query Name when we create a debugging tool rule.
{% endhint %}

## 2. GraphQL Prettier

From Proxyman 2.33.0, Proxyman can prettify/beautify GraphQL's Query Value. To do it, please open Tools Menu -> Custom Previewer Tab -> Check GraphQL checkbox.

![Beautify GraphQL Query](../.gitbook/assets/Screen\_Shot\_2021-09-11\_at\_15\_58\_08.png)

## 3. Show GraphQL Query Name on the main table view

It's possible to extract and display the Query Name. Please Right-click on the Column Header and enable it.

![Query Name from GrapQL Request](../.gitbook/assets/Screen\_Shot\_2021-03-13\_at\_16\_20\_42.png)

{% content-ref url="../basic-features/custom-header-column.md" %}
[custom-header-column.md](../basic-features/custom-header-column.md)
{% endcontent-ref %}

## 4. Debug GraphQL Requests (Legacy - Proxyman 2.26.0 and below)

GraphQL uses the same URL to query different responses from the server, current debugging tools (e.g. Map Local, Breakpoint, Map Remote) doesn't work well.

However, by using the Scripting Tool, we can easily achieve:

* Map Local for the response depends on QueryName
* Manipulate the query, body, header for GraphQL Requests and Response

### Map Local with the Scripting Tool

We can use the Scripting tool to map&#x20;

1. Open Proxyman
2. Enable SSL Proxying on the GraphQL domain
3. Verify that you can see HTTPS requests from your domain
4. Right-Click on the flow -> Tool -> Scripting to create a script with the given URL
5. To import a local file: Click the More button -> Import JSON or Other files -> Then selecting your file
6. Use the following script shows you how to set a Local File to a GraphQL request with QueryName="user"

```javascript
// Import file from More Button -> Import JSON or Other files 
const file = require("@users/B02D96D5.default_message_32E64A5B.json");

function onRequest(context, url, request) {

  // 1. Extract the queryName from the request
  var queryName = request.body.query.match(/\S+/gi)[1].split('(').shift();
  
  // Or extract the operationName
  var operationName = request.body.operationName
  
  // 2. Save to sharedState
  sharedState.queryName = queryName
  sharedState.operationName = operationName
  
  // Done
  return request;
}

function onResponse(context, url, request, response) {

  // 3. Check if it's the request we need to map
  if (sharedState.queryName == "user") {
    
    // 4. Import the local file by Action Button -> Import
    // Get the local JSON file and set it as a body (like Map Local)
    response.headers["Content-Type"] = "application/json";
    response.body = file;
  }

  // Done
  return response;
}
```

### Manipulate Headers, Query, Body

1. Use the same code and change the queryName&#x20;
2. Please use [the snipped code](../scripting/snippet-code.md#2-common-on-request-and-response) to change the values
