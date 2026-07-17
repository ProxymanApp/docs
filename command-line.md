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
By default, the `export` command will export all rules. To exclude particular rules, please uncheck the "Enabled" column in each debugging tool and use the `-m enabledRules`
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
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m all -o "~/desktop/output" --format raw
```
{% endcode %}

* Export All - HAR Format

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m domains -o "~/desktop/output" --domains 'api.twitter.com' --domains 'www.producthunt.com' --format har
```
{% endcode %}

* Export certain domains - RAW Request/Response Format

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m all -o "~/desktop/output" --format raw
```
{% endcode %}

* Export certain domains - HAR Format

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m domains -o "~/desktop/output" --domains 'api.twitter.com' --domains 'www.producthunt.com' --format raw
```
{% endcode %}

**From macOS 6.2.0+, we can export with a flag `--since <last_flow_id>` to only export from this flow ID.**

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

### 10. Export Current IP and Port

* Available from macOS 7.6.0 or later
* Get the current Listening IP & Port in JSON format

<pre class="language-bash"><code class="lang-bash"><strong>/Applications/Proxyman.app/Contents/MacOS/proxyman-cli proxy-host
</strong></code></pre>

### 11. Add, Remove, Replace the Custom certificates (Client and Server)&#x20;

* Available on macOS 6.10.0 or later ✅
* Support the P12 certificate with a password

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli custom-cert add server ~/Desktop/mycert.p12 --password 123

/Applications/Proxyman.app/Contents/MacOS/proxyman-cli custom-cert add client ~/Desktop/mycert.p12 --password 123 --host myserver.com --port 443

/Applications/Proxyman.app/Contents/MacOS/proxyman-cli custom-cert replace server ~/Desktop/mycert.p12 --password 123 --name mycert.p12

/Applications/Proxyman.app/Contents/MacOS/proxyman-cli custom-cert replace client ~/Desktop/mycert.p12 --password 123 --host myserver.com --port 443

/Applications/Proxyman.app/Contents/MacOS/proxyman-cli custom-cert remove server --name mycert.p12

/Applications/Proxyman.app/Contents/MacOS/proxyman-cli custom-cert remove client --host myserver.com --port 443
```
{% endcode %}

### 12. External Proxy CLI

* Proxyman macOS6.12.0 or later ✅

#### Enable

Enable External Proxy without changing the saved configuration:

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy enable
```

* Enable and configure a proxy mode:

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy enable http --host proxy.example.com --port 8080
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy enable https --host proxy.example.com --port 8443
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy enable socks --host proxy.example.com --port 1080
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy enable pac --url https://example.com/proxy.pac
```

#### Disable

Disable the entire External Proxy feature:

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy disable
```

* Disable only one proxy mode:

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy disable http
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy disable https
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy disable socks
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy disable pac
```

### 13. CRUD for all debugging tools

{% hint style="success" %}
Only available on Proxyman macOS 6.14.0 or later
{% endhint %}

#### Supported tools

`block-list`, `allow-list`, `ssl-proxying`, `map-local`, `map-remote`, `breakpoint`, `scripting`, `network-condition`, `reverse-proxy`, `protobuf`, and `dns-spoofing`.

#### Common commands

Replace `<tool>` with one of the supported tools and `<id>` with a rule ID from `list` or `get`.

```bash
# Read rules
proxyman-cli rules <tool> list
proxyman-cli rules <tool> list --enabled true
proxyman-cli rules <tool> get <id>

# Change one rule
proxyman-cli rules <tool> update <id> --name "New name"
proxyman-cli rules <tool> delete <id>

# Turn a whole tool on or off
proxyman-cli rules <tool> enable
proxyman-cli rules <tool> disable

# Turn one rule on or off
proxyman-cli rules <tool> enable <id>
proxyman-cli rules <tool> disable <id>
```

`enable <id>` also turns on its tool when needed. Turning off a tool keeps each rule's own enabled setting. Updates change only the fields you send; delete removes the rule right away.

#### Create a rule

These are the smallest create commands. Optional flags let you set more fields. Run `proxyman-cli rules <tool> create --help` to see them.

```bash
proxyman-cli rules block-list create https://ads.example.com/*
proxyman-cli rules allow-list create https://api.example.com/*
proxyman-cli rules ssl-proxying create '*.example.com' --list include
proxyman-cli rules map-local create https://api.example.com/* --path ./response.json
proxyman-cli rules map-remote create https://old.example.com/* https://new.example.com/
proxyman-cli rules breakpoint create https://api.example.com/* --phase both
proxyman-cli rules scripting create https://api.example.com/* --script-file ./rule.js
proxyman-cli rules network-condition create --profile 3g
proxyman-cli rules reverse-proxy create https://upstream.example.com --local-port 8080
proxyman-cli rules protobuf create https://api.example.com/* --request-type package.Request
proxyman-cli rules dns-spoofing create example.com 127.0.0.1
```

Common rule flags include `--name`, `--enabled true|false`, `--method`, `--match wildcard|regex`, and `--include-subpaths true|false` when the tool supports them. Names are optional. If you omit an optional value, Proxyman uses that tool's normal default.

#### JSON input

For create and update, use `--input <file>` to send a JSON object. Use `--input -` to read JSON from standard input. Do not mix `--input` with field flags.

```bash
printf '%s' '{"url":"https://api.example.com/*","name":"Local API","enabled":true}' \\
  | proxyman-cli rules map-local create --input -

proxyman-cli rules map-local update <id> --input ./map-local-change.json
```

When Proxyman is closed, the command returns JSON with `ok: false` and the `app_not_running` error code. Input errors use exit code `2`; other errors use exit code `1`.
