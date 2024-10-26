---
description: >-
  How to export and Import data from Proxyman. Support Proxyman Log, HAR, CSV,
  Charles File, PostmanCollection2
---

# Import / Export

### 1. Import

Proxyman supports multiples traffic log files from Proxyman and Charles Proxy.

* **Proxyman Log**: Built-in Proxyman Log that contains all Requests and Responses information.
* Proxyman Session: Entire working session files that are exported from the Proxyman app.
* **HAR 1.2** ([HTTP Archive](https://en.wikipedia.org/wiki/HAR\_\(file\_format\))): Suitable for transferring the HTTP Request and Response to other apps for the later inspector. Charles, Google Chrome, Safari, Firefox, and other Network Analyzer apps are fully supported.
* **Charles Proxy Log**: Charles Log that exports from Charles Proxy app. The file extension is **chls**.
* **CSV File**: Export selected requests as a CSV file (Proxyman 2.29.0+)
* **Charles Proxy Log for iOS** (Proxyman 2.30.0+): File extension is **chlsj**.
* Export as Postman Collection 2.

If you would like to save an entire working Session, please read the Save Session Page.

{% content-ref url="../advanced-features/save-session.md" %}
[save-session.md](../advanced-features/save-session.md)
{% endcontent-ref %}

{% content-ref url="../advanced-features/charles-proxy-converter.md" %}
[charles-proxy-converter.md](../advanced-features/charles-proxy-converter.md)
{% endcontent-ref %}

### 2. Export

You can export:

* List of selected Requests or Responses.
* All traffic from specific Client or Domain Node or Remote Devices.
* An entire working session.
* Export as Proxyman LOG or ProxymanSession, Body or Raw tab.

It's useful to export a bug request that you can investigate later or send to your QA team.

### 3. Import & Export by Command Line

Proxyman offers a useful command line that helps you perform that import/export operation by a bash script.

{% content-ref url="../command-line.md" %}
[command-line.md](../command-line.md)
{% endcontent-ref %}

### 4. How to use

#### 4.1 Import files to Proxyman

* **Drag and drop** files to Proxyman Window
* File -> Open -> Select a file

The imported file will be added to the Pin Section where you can inspect all traffic.

#### 4.2 Export to files

There are many ways to export a selected request to files:

* Select Request & Response on the main table view -> Right Click -> Export
* Right Click on the App or Domain -> Export&#x20;

![](../.gitbook/assets/Screen\_Shot\_2021-08-27\_at\_13\_56\_53.png)

