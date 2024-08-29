# Lost data after updating Proxyman app?

### Problem

After updating the app to the latest version, you might encounter:

* Your current data, including all debugging tools rules (Map Local, Scripting, Breakpoint, SSL Proxying List, ...) and user settings, etc are wiped out.

{% hint style="info" %}
Proxyman will **guarantee** that your current data **is never lost**. However, it's still better if we have the backup of your valuable data ⚡️.
{% endhint %}

### How to recover

1. Open the backup folder at `~/Library/Application Support/com.proxyman.NSProxy/user-data-backups`
2. Unzip the latest backup file (You can sort by the "Add Date" in the Finder app. It will show the latest backup).
3. Copy each folder of the backup folder to the app folder at `~/Library/Application Support/com.proxyman.NSProxy`

For instance:

<table><thead><tr><th width="186.4852062786498">Copy From</th><th>Copy To</th></tr></thead><tbody><tr><td>~/Library/Application Support/com.proxyman.NSProxy/user-data-backups/userdata_proxyman_3.6.0_05-24-2022-11-55-20/user-data</td><td>~/Library/Application Support/com.proxyman.NSProxy/user-data</td></tr><tr><td>~/Library/Application Support/com.proxyman.NSProxy/user-data-backups/userdata_proxyman_3.6.0_05-24-2022-11-55-20/map-local</td><td>~/Library/Application Support/com.proxyman.NSProxy/map-local</td></tr><tr><td>and more...</td><td></td></tr></tbody></table>

### When does Proxyman backup my data?

After you update Proxyman to a newer version, Proxyman might backup your current data and save at `~/Library/Application Support/com.proxyman.NSProxy/user-data-backups`
