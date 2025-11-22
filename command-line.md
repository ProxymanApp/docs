---
description: Interact with Proxyman via Command Line.
---

# Command-line

Proxyman provides a useful command-line tool to enhance your onboarding experience ✅.

You can access the tool at `/Applications/Proxyman.app/Contents/MacOS/proxyman-cli`

## 1. Export Proxyman config

Export all debugging tools rules, such as SSL Proxying List, Breakpoint, Map Local, Scripting, Block List, Allow List, Reverse Proxy, and Network Conditions.

```bash
$ /Applications/Proxyman.app/Contents/MacOS/proxyman-cli export -h

OVERVIEW: Export all debugging tools rules (Breakpoint, SSL Pinning, Map Local, Map
Remote, Scripting, etc).

USAGE: proxyman-cli export [--mode <mode>] --output <output>

OPTIONS:
  -m, --mode <mode>       Export Mode (all = "All debugging tools's rules", enabledRules
                          = "Only enabled rules"). (default: all)
  -o, --output <output>   A Output file to save the config to.
  --version               Show the version.
  -h, --help              Show help information.
```

{% hint style="info" %}
By default, the `export` command will export all rules. To exclude particular rules, please uncheck the "Enabled" column in each debugging tool and use the `-m  enabledRules`
{% endhint %}

#### For example:

* Export all debugging tool rules:

`$ /Applications/Proxyman.app/Contents/MacOS/proxyman-cli export -o ~/Desktop/data.json`

* Only export enabled rules:

`$ /Applications/Proxyman.app/Contents/MacOS/proxyman-cli export -m enabledRules -o ~/Desktop/data.json`

## 2. Import Proxyman config

Import Proxyman debugging tools rules that you have exported by the export command.

```bash
$ /Applications/Proxyman.app/Contents/MacOS/proxyman-cli import -h

OVERVIEW: Import config to Proxyman.

USAGE: proxyman-cli import [--mode <mode>] --input <input>

OPTIONS:
  -m, --mode <mode>       Import Mode (append = "Append to the existing rules"),
                          override = "Import and Replace all existing rules". (default:
                          append)
  -i, --input <input>     A input file to import.
  --version               Show the version.
  -h, --help              Show help information.
```

{% hint style="info" %}
By default, new imported rules will be appended to the existing debugging rules. To override all rules, let use `-m override`
{% endhint %}

#### For example:

* Import all debugging rules by appending them:

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli import -i ~/Desktop/data.json
```
{% endcode %}



* Import, but override all my existing rules:

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli import -m override -i ~/Desktop/data.json
```
{% endcode %}



## 3. Activate/Unlink License

Please check out the command for activating and unlinking a license.

{% content-ref url="license.md" %}
[license.md](license.md)
{% endcontent-ref %}

## 4. Toggle HTTP System Proxy

From Proxyman 4.8.0 and later, we can toggle the Proxy System by command line. It's useful for Raycast Extension

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli proxy on
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli proxy off
```

Reference: [https://github.com/ProxymanApp/Proxyman/issues/1626#issuecomment-1545862020](https://github.com/ProxymanApp/Proxyman/issues/1626#issuecomment-1545862020)

## 5. Clear Session

* We can clear the current Session from the command line. Available for Proxyman 4.12.0 and later.

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli clear-session
```

## 6. Toggle Debugging Tools

* Toggle Breakpoint, Map Local, and Scripting Tool by command line. Available for Proxyman 4.12.0 and later.

```bash
# Scripting
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli scripting on
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli scripting off

# Map Local
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli maplocal on
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli maplocal off

# Breakpoint
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli breakpoint on
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli breakpoint off
```

## 7. Install the Proxy Helper Tool by command line

From macOS 4.12.0 or later, you can install the Helper Tool without GUI.

{% code overflow="wrap" %}
```bash
sudo /Applications/Proxyman.app/Contents/MacOS/proxyman --install-privileged-components
```
{% endcode %}

## 8. Export Proxyman Log

**Proxyman macOS v5.11.0+ now supports:**

* Export all (ProxymanSession Format)

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m all -o "~/desktop/output"
```
{% endcode %}

* Export certain domains (Only Host, no scheme, no port, no paths, and no Query)

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m domains -o "~/desktop/output" --domains 'api.twitter.com' --domains 'www.producthunt.com'
```
{% endcode %}

**From Proxyman macOS 5.20.0+, we can export with Raw or HAR format.**

* Export All - RAW Request/Response Format

{% code overflow="wrap" %}
```
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m all -o "~/desktop/output" --format raw
```
{% endcode %}

* Export All - HAR Format

{% code overflow="wrap" %}
```
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m domains -o "~/desktop/output" --domains 'api.twitter.com' --domains 'www.producthunt.com' --format har
```
{% endcode %}

* Export certain domains - RAW Request/Response Format

{% code overflow="wrap" %}
```
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m all -o "~/desktop/output" --format raw
```
{% endcode %}

* Export certain domains - HAR Format

{% code overflow="wrap" %}
```
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m domains -o "~/desktop/output" --domains 'api.twitter.com' --domains 'www.producthunt.com' --format raw
```
{% endcode %}

## 9. Import Custom Root Certificate

* ✅ Import Custom p12 Root Certificate to Proxyman
* Automatically Trust the certificate in System Keychain (sudo required)
* Available from Proxyman macOS 5.15.0 or later

#### Install and trust

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli install-root-cert <certificate_path> --password <your_cert_password> --trust
```
{% endcode %}

#### Install but not trust (you might need to trust it manually in the Keychain)

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli install-root-cert <certificate_path> --password <your_cert_password>
```
{% endcode %}

<br>



