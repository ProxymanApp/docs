# Command-line

Proxyman provides a useful command-line tool to enhance your onboarding experience ✅.

You can access the tool at `/Applications/Proxyman.app/Contents/MacOS/proxyman-cli`

### 1. Export Proxyman config

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
By default, the `export` command would export all rules. To exclude particular rules, please uncheck the "Enabled" column in each debugging tool and use the `-m  enabledRules`
{% endhint %}

#### For example:

* Export all debugging tool rules:

`$ /Applications/Proxyman.app/Contents/MacOS/proxyman-cli export -o ~/Desktop/data.json`

* Only export enabled rules:

`$ /Applications/Proxyman.app/Contents/MacOS/proxyman-cli export -m enabledRules -o ~/Desktop/data.json`

### 2. Import Proxyman config

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

`$ /Applications/Proxyman.app/Contents/MacOS/proxyman-cli import -i ~/Desktop/data.json`

* Import, but override all my existing rules:

`$ /Applications/Proxyman.app/Contents/MacOS/proxyman-cli import -m override -i ~/Desktop/data.json`

### 3. Activate/Unlink License

Please check out the command for activating and unlinking a license.

{% content-ref url="license.md" %}
[license.md](license.md)
{% endcontent-ref %}

### 4. Toggle HTTP System Proxy

From Proxyman 4.8.0 and later, we can toggle the Proxy System by command line. It's useful for Raycast Extension

```
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli proxy on
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli proxy off
```

Reference: [https://github.com/ProxymanApp/Proxyman/issues/1626#issuecomment-1545862020](https://github.com/ProxymanApp/Proxyman/issues/1626#issuecomment-1545862020)

### 5. Clear Session

* We can clear the current Session from the command line. Available for Proxyman 4.12.0 and later.

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli clear-session
```

### 6. Toggle Tools

* Toggle Breakpoint, Map Local, and Scripting Tool by command line. Available for Proxyman 4.12.0 and later.

```
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

### 7. Install the Proxy Helper Tool by command line

From macOS 4.12.0 or later, you can install the Helper Tool without GUI.

```
sudo /Applications/Proxyman.app/Contents/MacOS/proxyman --install-privileged-components
```
