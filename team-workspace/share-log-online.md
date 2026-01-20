---
description: How to share HAR, Proxyman Log to your teammates, and preview it online
---

# Share Log online

## 1. What’s it?

Proxyman HTTP Logs is the workspace feature that lets you upload, store, and share Proxyman HTTP capture files so you (and your team) can review issues with consistent context.

Supported uploads:

* .proxymanlogv2, .proxymansessionv2, .har
* Max file size: 50 MB per upload

After a successful upload, the UI guides you through:

1. Adding an optional note (Markdown supported)

<figure><img src="../.gitbook/assets/Screenshot 2026-01-20 at 16.26.43.png" alt="Add note to your log"><figcaption></figcaption></figure>

2. Setting sharing permissions

<figure><img src="../.gitbook/assets/Screenshot 2026-01-20 at 16.26.49.png" alt=""><figcaption></figcaption></figure>



### Sharing & permissions model

Each log can be shared as:

* **Private**: only permitted viewers can access (default when no sharing is set)
* **Team**: all workspace members can view
* **Specific users**: only selected teammates can view (by email)
* **Public**: anyone with the share link can view

Important rules:

* A log has a share link: /shared/\<log-id>
* Only the uploader can change sharing settings for that log (others can view if they have access, but can’t change permissions)

#### Roles (role-based access)

* Admin
* Full workspace access (licenses, logs, settings, team)
* Can view logs they have access to
* Can manage sharing only for logs they uploaded (uploader-only rule still applies)
* Developer
* Can view logs shared with them (via Team, Specific users, or Public link)
* Can upload logs and manage sharing only for logs they uploaded

\> Team Subscription plan note: “Team” and “Specific users” sharing is designed for Team-plan workspaces where you have teammates in the workspace (seat-based access).

***

### 2. Benefit

* Fast collaboration: upload a capture once, share it with your team instantly.
* Clear context: add a note (Markdown supported) to explain what to look for.
* Flexible sharing: keep logs private, share to the whole team, specific teammates, or publicly via link.
* Simple organization: see filename, size, uploader, sharing state, and relative upload time in one table.
* Storage safety: when quota is exceeded, the UI tells you how to recover (delete old logs or contact support to upgrade quota).

<figure><img src="../.gitbook/assets/Screenshot 2026-01-20 at 16.32.57.png" alt="Sharing Log with your teammates"><figcaption></figcaption></figure>

***

### 3. How to use it

#### 1. Upload a log

You can upload in two ways:

* Click “Upload Log” / “Browse Files”
* Drag & drop the file into the drop zone

The page validates:

* File type (.proxymanlogv2, .proxymansessionv2, .har)
* File size (≤ 50 MB)

#### 2. Add a note (optional)

After upload completes, a dialog opens to add a note:

* Supports basic Markdown (bold/italic/code/lists/links)
* Has a character limit (the UI will block saving if you exceed it)
* You can preview the rendered Markdown before saving

#### 3. Configure sharing

After the note dialog closes, the Share Log dialog opens. You can:

* Toggle Public Access (anyone with the link can view)
* Toggle Team Access (all team members can view)
* Add Specific Users (only teammates in the workspace; you must invite them first)

Then click Save Changes. Notes:

* You can only add emails that belong to teammates already in your workspace
* Only the uploader can change these settings

#### View, download, copy link, or delete

In Your Shared Logs, each log supports:

* Open the log details: click the filename (goes to /logs/\<log-id>)
* Manage Sharing
* Add/Edit Note
* Download
* Copy Share Link (copies /shared/\<log-id>)
* Delete (with confirmation; cannot be undone)

#### If the storage quota is exceeded

If you hit the workspace storage limit during upload, you’ll see Storage Quota Exceeded with options to:

* Delete old log files to free space
* Contact support@proxyman.com to upgrade storage quota
