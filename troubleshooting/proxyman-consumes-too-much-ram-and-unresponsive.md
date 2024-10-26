---
description: Solution to fix memory issue when using Proxyman
---

# Proxyman consumes too much RAM & unresponsive

## Problems

If Proxyman is:

* Unresponsive after using it for a while.
* Consume too much Memory.

You might encounter the above problems if you enable SSL Proxying with the following rules:

* Use the all \`\*\` wildcard to intercept all traffic from your Mac Machine.
* Enable the entire web browser (Google Chrome, Safari, Firefox, etc.).

## **Reason**

Proxyman will intercept and decrypt all traffic which leads to high memory usage. In the worst scenario, the app can become unresponsive.

![SSL Proxying List with web browser or \* wildcard can slow your Mac.](../.gitbook/assets/Screen\_Shot\_2022-08-10\_at\_14\_01\_16.png)

## Solution

1. ✅ Update to the latest Proxyman version (Memory Leaks has been fixed in the latest builds)
2. Open Tools -> SSL Proxying List&#x20;
3. Remove all Web Browser or \`\*\` wildcards if they exist.
4. Enable SSL Proxying on particular domains.
