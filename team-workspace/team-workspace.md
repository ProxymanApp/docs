---
description: >-
  Use Proxyman Team Workspace to invite teammates, give them Admin or Developer
  roles, track seat usage and share licenses and logs with your team.
---

# Team Workspace

## 1. What’s it?

Team Management is the workspace feature that lets you manage who can access your workspace, what role they have, and how many seats you’re using.

{% hint style="info" %}
&#x20;This feature is only available for the **Team Subscription plan** (seat-based)
{% endhint %}

<figure><img src="../.gitbook/assets/Screenshot 2026-01-20 at 15.48.56.jpg" alt="Proxyman Workspace Team page with seat usage, team members and their admin or developer roles"><figcaption></figcaption></figure>

### Roles (role-based access)

#### Admin

* Full access to everything: licenses, logs, team, and workspace settings
* Can view seat usage, invite members, bulk invite, change roles, remove members, and revoke invitations
* Only admins can access the Team page

#### Developer

* Can view the license key and all shared logs within the team
* Cannot access the Team management page (admin-only)

***

## 2. Benefit

* Centralized access control: keep workspace access managed in one place.
* Safer collaboration: assign roles so teammates only have the permissions they need.
* Seat visibility: see used / total seats, pending invitations, and remaining capacity.
* Fast onboarding: invite one person or bulk invite up to 50 emails at a time.
* Fewer mistakes: invitations expire in 24 hours, and bulk invite automatically skips emails that can't be invited (for example, no seats left, already registered, or already invited).

***

## 3. How to use it

### Open the Team page (admin-only)

1. Sign in to [Proxyman Workspace](https://workspace.proxyman.com) as an Admin.
2. Go to Settings → Team.

If you’re not an admin, you’ll see an “Admin access required” message.

### Check seat usage (Team plan)

* Review the Seat Usage card:
  * Used / Total seats
  * Available seats
  * Pending invitations
* When seats are low or full, the UI warns you before inviting.

### Invite a single member

1. Click Invite Member.
2. Enter the teammate’s email.
3. Choose a role:
   * Developer (license key + shared logs)
   * Admin (full access)
4. Click Send Invitation.

Notes:

* Invitation links expire in 24 hours.
* If there are 0 seats available, inviting is blocked and you’ll be prompted to add seats.

<figure><img src="../.gitbook/assets/Screenshot 2026-01-20 at 15.52.15.png" alt="Invite Team Member dialog with an email address field and the Developer role selected"><figcaption></figcaption></figure>

### Bulk invite (up to 50)

1. Click Bulk invite.
2. Paste emails comma-separated (max 50).
3. Choose a role for all invited emails.
4. Click Schedule invitations (sent shortly to avoid spam filters).

After scheduling, the UI shows how many were scheduled and which ones were skipped (with reasons like no seats, already registered, already invited).

### Change a member’s role (admin-only)

1. In Team Members, open the role dropdown for a member.
2. Select Developer or Admin.

The current user’s own role is displayed but not editable from this page.

### Remove a team member (admin-only)

1. In Team Members, open the actions menu for a member.
2. Click Remove member and confirm.

Result: the member loses access to all workspace resources.

### Revoke a pending invitation (admin-only)

1. In Pending Invitations, click the trash icon for an invitation.
2. Confirm Revoke.

Result: the invite link becomes unusable.

### Buy more seats (Team plan)

* Click Buy More Seats (or Extend Seats when you hit seat limits).
* Complete the seat upgrade flow.
* The page refreshes seat usage and team data after success.

<figure><img src="../.gitbook/assets/Screenshot 2026-01-20 at 15.53.04.png" alt="Extend Subscription Seats dialog to add seats, with current and new seat totals and the prorated charge"><figcaption></figcaption></figure>

Your team can also share captured logs in the workspace. See [Share Log online](share-log-online.md).
