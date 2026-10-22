---
description: >-
  Install WSL, Chocolatey (choco) and adb on Windows 10 or 11 so you can use the
  Proxyman automatic script for Android Emulators.
---

# WSL

## 1. What's it?

To use the Automatic Script for Android Emulator in Proxyman for Windows, the following command-line tools must be installed on your Windows machine:

* wsl
* choco (package manager for Windows)
* adb (Android Debug Bridge)

## 2. Install WSL on Windows 10/11

1. On Windows 10/11, search: **Command Prompt** app
2. Right-click on the app -> Select **Run as administrator** option.
3. When the app opens, copy and paste the following command:

```bash
wsl --install
```

4. Restart Windows to apply the change -> After restarting, Windows opens the **Command Prompt** and asks you to create a new Username / Password -> Follow the instructions
5. Open the Command Prompt app again and run:

```
wsl
```

6. Verify that the command is successful, with no errors:

<figure><img src="../.gitbook/assets/CleanShot 2024-03-29 at 9 .43.29@2x.jpg" alt="Windows Terminal after running wsl, showing the Linux shell prompt with no errors"><figcaption></figcaption></figure>

7. Done ✅

## 3. Install **Choco** on Windows 10/11

1. Open PowerShell with Run as Administrator
2. Paste and run it:

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

3. Wait a few seconds for the command to complete.&#x20;
4. If you don't see any errors, you are ready to use Chocolatey! Type `choco` or `choco -?` to check it.

Choco Installation Guide: [https://chocolatey.org/install#individual](https://chocolatey.org/install#individual)

## 4. Install **adb** on Windows 10/11

1. Open PowerShell with Run as Administrator
2. Run:

```
choco install adb -y
```

3. Verify that **adb** is installed and there is no error

## 5. ✅ Done. Try the Android Automatic Script again in the Proxyman app

## 6. References:

* [https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)
* [https://pureinfotech.com/install-wsl-windows-11/#install\_wsl2\_single\_command](https://pureinfotech.com/install-wsl-windows-11/#install\_wsl2\_single\_command)
