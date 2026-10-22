---
description: >-
  Import and export traffic in Proxyman: open Proxyman Log, HAR and Charles
  files, and export requests as Proxyman Log, HAR, CSV or Postman Collection.
---

# Import / Export

## 1. Import

Proxyman can open traffic log files from Proxyman, Charles Proxy, and other apps that export HAR files.

* **Proxyman Log**: Built-in Proxyman Log that contains all Requests and Responses information.
* **Proxyman Session**: Entire working session files that are exported from the Proxyman app.
* **HAR 1.2** ([HTTP Archive](https://en.wikipedia.org/wiki/HAR\_\(file\_format\))): Useful for moving HTTP requests and responses between apps to inspect later. Charles, Google Chrome, Safari, Firefox, and other network analyzer apps are fully supported.
* **Charles Proxy Log**: Charles log exported from the Charles Proxy app. The file extension is **chls**.
* **Charles Proxy Log for iOS** (Proxyman 2.30.0+): The file extension is **chlsj**.

If you would like to save an entire working session, please read the Save Session page.

{% content-ref url="../advanced-features/save-session.md" %}
[save-session.md](../advanced-features/save-session.md)
{% endcontent-ref %}

{% content-ref url="../advanced-features/charles-proxy-converter.md" %}
[charles-proxy-converter.md](../advanced-features/charles-proxy-converter.md)
{% endcontent-ref %}

## 2. Export

You can export:

* A list of selected requests or responses.
* All traffic from a specific client, domain node, or remote device.
* An entire working session.
* The Body or Raw content of a request or response.

Export formats:

* **Proxyman Log** or **Proxyman Session**
* **HAR** (HTTP Archive)
* **CSV File**: Export selected requests as a CSV file (Proxyman 2.29.0+)
* **Postman Collection 2**

It's useful to export a buggy request that you can investigate later or send to your QA team.

## 3. Import & Export by Command Line

Proxyman offers a command line tool that lets you import and export from a bash script.

{% content-ref url="../command-line.md" %}
[command-line.md](../command-line.md)
{% endcontent-ref %}

## 4. How to use

### 4.1 Import files to Proxyman

* **Drag and drop** files to the Proxyman window
* **File** → **Open…** (⌘O) → Select a file

The imported file is added to the Pinned section in the sidebar, where you can inspect all traffic.

### 4.2 Export to files

There are many ways to export the selected requests to files:

* Select requests in the main table → Right-click → **Export**
* Right-click the app or domain in the sidebar → **Export**&#x20;
* Select requests → **Flow** → **Export** in the menu bar

![Proxyman request context menu with the Export submenu showing as Proxyman Log, HAR, CSV and Postman](../.gitbook/assets/Screen\_Shot\_2021-08-27\_at\_13\_56\_53.png)

## Learn more

* [How to open the HAR file from Google Chrome](https://proxyman.com/posts/2026-06-16-How-to-open-the-HAR-file-from-Google-Chrome)
* [Migrate from Charles to Proxyman](https://proxyman.com/posts/2020-07-03-Migrate_From_Charles_To_Proxyman)
