---
description: >-
  Lost your Proxyman rules or settings after an update? Restore Map Local,
  Scripting, Breakpoint and other data from Proxyman's automatic backup folder.
---

# Lost data after updating Proxyman app?

## Problem

After updating the app to the latest version, you might see that:

* Your data, including all debugging tool rules (Map Local, Scripting, Breakpoint, SSL Proxying List, ...) and user settings, is wiped out.

{% hint style="info" %}
Proxyman makes sure your data **is never lost**. Still, it's good to have a backup of your valuable data ⚡️.
{% endhint %}

## How to recover

1. Open the backup folder at `~/Library/Application Support/com.proxyman.NSProxy/user-data-backups`
2. Unzip the latest backup file. (In Finder, sort by "Date Added" to find the latest backup.)
3. Copy each folder from the backup to the app folder at `~/Library/Application Support/com.proxyman.NSProxy`

For instance:

<table><thead><tr><th width="186.4852062786498">Copy From</th><th>Copy To</th></tr></thead><tbody><tr><td>~/Library/Application Support/com.proxyman.NSProxy/user-data-backups/userdata_proxyman_3.6.0_05-24-2022-11-55-20/user-data</td><td>~/Library/Application Support/com.proxyman.NSProxy/user-data</td></tr><tr><td>~/Library/Application Support/com.proxyman.NSProxy/user-data-backups/userdata_proxyman_3.6.0_05-24-2022-11-55-20/map-local</td><td>~/Library/Application Support/com.proxyman.NSProxy/map-local</td></tr><tr><td>and more...</td><td></td></tr></tbody></table>

A backup contains the `user-data`, `map-local`, `scripts` and `users` folders.

{% hint style="info" %}
If you use Proxyman from Setapp, the app folder is `~/Library/Application Support/com.proxyman.NSProxy-setapp`.
{% endhint %}

## When does Proxyman back up my data?

After you update Proxyman to a newer version, Proxyman backs up your current data and saves it to `~/Library/Application Support/com.proxyman.NSProxy/user-data-backups`.

To make your own backup at any time, use **Tools** -> **Import / Export Settings** -> **Export (Backup)…**. See [Import / Export Settings](../basic-features/import-export-settings.md).
