---
description: >-
  Back up and share Proxyman settings and debugging rules, import rules from
  Proxyman or Charles Proxy, and open Charles Proxy session files.
---

# Import / Export Settings

## 1. Import Settings

From Proxyman 2.26.0, you can import tool settings from colleagues who use **Proxyman** or **Charles Proxy**.&#x20;

To import settings, go to **Tools** → **Import / Export Settings** → **Import**, then choose **From Proxyman** or **From Charles Proxy**:

* **From Proxyman** → **From Backup File**: Import a `.config` backup file made with **Export (Backup)**. Choose **Override** to replace your current settings, or **Append** to add to them.
* **From Proxyman** → **Single Rule (Deprecated)**, or **From Charles Proxy**: Select the tool you want to import.

![Tools menu of an older Proxyman version with Import Settings submenus for Proxyman and Charles Proxy](../.gitbook/assets/Screen\_Shot\_2021-05-17\_at\_09\_11\_44.png)

You can import settings for these tools:

### Proxyman

* SSL Proxying List
* Block List
* Allow List (White List)
* Map Local
* Map Remote
* Breakpoint
* Network Conditions
* Scripting
* Reverse Proxy
* DNS Spoofing
* Protobuf

### Charles Proxy

* SSL Proxying List
* Block List
* Allow List (White List)
* Map Local
* Map Remote
* Breakpoint
* Reverse Proxy
* DNS Spoofing

## 2. Export Settings

You can also export your tool settings and share them with your colleagues.

### Back up all settings

From Proxyman 6.4.0, you can save your app settings and debugging tools in one backup file:

1. Go to **Tools** → **Import / Export Settings** → **Export (Backup)…**
2. Select **App Settings** and the debugging tools you want to include
3. Click **Export** and save the `.config` file

### Export rules from one tool

1. Open the tool you want to export
2. Select the rules
3. Right-click → **Export Settings…**

![Block List window with a rule selected and Export Settings in the context menu](../.gitbook/assets/Screen\_Shot\_2021-05-17\_at\_09\_16\_41.png)

## 3. Open Charles Proxy Log File (\*.chls)

Proxyman can open Charles Proxy log files that you export from the Charles Proxy app. Read the Charles Proxy Converter page.

{% content-ref url="../advanced-features/charles-proxy-converter.md" %}
[charles-proxy-converter.md](../advanced-features/charles-proxy-converter.md)
{% endcontent-ref %}

## Learn more

* [Migrate from Charles to Proxyman](https://proxyman.com/posts/2020-07-03-Migrate_From_Charles_To_Proxyman)
* [Hidden features from Proxyman: import Charles Proxy log files](https://proxyman.com/posts/2021-07-03-hidden-features-from-proxyman)
