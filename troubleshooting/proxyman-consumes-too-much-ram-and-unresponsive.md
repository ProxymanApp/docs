# Proxyman consumes too much RAM & unresponsive

### Problems

If Proxyman is:

* Unresponsive after using for a while.
* Consume too much Memory.

You might encounter above problems if you enable SSL Proxying with the following rules:

* Use the all \`\*\` wildcard to intercept all traffic from your Mac Machine.
* Enable for entire Web Browser (Google Chrome, Safari, Firefox, etc).

### **Reason**

Proxyman will intercept and decrypt all traffic which leads to high memory usage. In the worst scenario, the app can become unresponsive.

![SSL Proxying List with web browser or \* wildcard can slow your Mac.](../.gitbook/assets/Screen\_Shot\_2022-08-10\_at\_14\_01\_16.png)

### Solution

1. Open Tools -> SSL Proxying List&#x20;
2. Remove all Web Browser or \`\*\` wildcard if it exists.
3. Enable SSL Proxying on particular domains.
