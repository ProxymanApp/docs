---
description: >-
  Use proxyman-cli to control Proxyman for macOS from Terminal: export and
  import rules, toggle tools and the system proxy, export logs and manage certs.
---

# Command-line

Proxyman for macOS comes with `proxyman-cli`, a command-line tool to control Proxyman from Terminal and your own scripts ✅.

You can access the tool at `/Applications/Proxyman.app/Contents/MacOS/proxyman-cli`

To see all commands for your installed version, run:

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli --help
```

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

### For example:

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
By default, new imported rules will be appended to the existing debugging rules. To override all rules, use `-m override`
{% endhint %}

### For example:

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

See the License page for the commands to activate and unlink a license.

{% content-ref url="license.md" %}
[license.md](license.md)
{% endcontent-ref %}

## 4. Toggle HTTP System Proxy

From Proxyman 4.8.0 and later, you can turn the macOS System Proxy on or off from the command line. The [Raycast extension](raycast.md) uses it.

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli proxy on
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli proxy off
```

Reference: [https://github.com/ProxymanApp/Proxyman/issues/1626#issuecomment-1545862020](https://github.com/ProxymanApp/Proxyman/issues/1626#issuecomment-1545862020)

## 5. Clear Session

* You can clear the current Session from the command line. Available for Proxyman 4.12.0 and later.

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

* From Proxyman macOS 6.3.0 or later, you can also toggle these tools the same way: `map-remote`, `block-list`, `allow-list`, `reverse-proxy`, `network-condition`, `no-caching`, and `dns-spoofing`.
* Use `open` instead of `on` or `off` to open the tool window, for example `proxyman-cli map-remote open`. `no-caching` only supports `on` and `off`.
* Proxyman must be running for these commands to work.

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli map-remote on
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli block-list off
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli network-condition open
```

## 7. Install the Proxy Helper Tool by command line

From Proxyman macOS 4.12.0 or later, you can install the Helper Tool without the GUI.

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

**From Proxyman macOS 5.20.0+, you can export with Raw or HAR format.**

* Export All - RAW Request/Response Format

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m all -o "~/desktop/output" --format raw
```
{% endcode %}

* Export All - HAR Format

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m all -o "~/desktop/output" --format har
```
{% endcode %}

* Export certain domains - RAW Request/Response Format

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m domains -o "~/desktop/output" --domains 'api.twitter.com' --domains 'www.producthunt.com' --format raw
```
{% endcode %}

* Export certain domains - HAR Format

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli export-log -m domains -o "~/desktop/output" --domains 'api.twitter.com' --domains 'www.producthunt.com' --format har
```
{% endcode %}

**From Proxyman macOS 6.2.0+, you can add `--since <flow_id>` to export only the flows from this flow ID onward (the flow with this ID is included). It works with all export formats.**

Supported formats for `--format` are `proxymansession` (default), `har`, and `raw`.

## 9. Import Custom Root Certificate

* ✅ Import Custom p12 Root Certificate to Proxyman
* Automatically Trust the certificate in System Keychain (sudo required)
* Available from Proxyman macOS 5.15.0 or later

### Install and trust

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli install-root-cert <certificate_path> --password <your_cert_password> --trust
```
{% endcode %}

### Install but not trust (you might need to trust it manually in the Keychain)

{% code overflow="wrap" %}
```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli install-root-cert <certificate_path> --password <your_cert_password>
```
{% endcode %}

## 10. Export Current IP and Port

* Available from Proxyman macOS 6.7.0 or later
* Get the current Listening IP & Port in JSON format

<pre class="language-bash"><code class="lang-bash"><strong>/Applications/Proxyman.app/Contents/MacOS/proxyman-cli proxy-host
</strong></code></pre>

The output has an `ip` and a `port` field, for example `{"ip":"192.168.1.10","port":9090}`. If Proxyman only listens on localhost, the IP is `127.0.0.1`.

## 11. Add, Remove, Replace the Custom certificates (Client and Server)&#x20;

* Available on Proxyman macOS 6.10.0 or later ✅
* Supports P12 certificates with a password
* For client certificates, `--port` defaults to `443`

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

## 12. External Proxy CLI

* Proxyman macOS 6.12.0 or later ✅

### Enable

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

### Disable

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

### Open the settings

Open the External Proxy settings window in Proxyman:

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli external-proxy open
```

## 13. CRUD for all debugging tools

{% hint style="success" %}
Only available on Proxyman macOS 6.14.0 or later
{% endhint %}

### Supported tools

`block-list`, `allow-list`, `ssl-proxying`, `map-local`, `map-remote`, `breakpoint`, `scripting`, `network-condition`, `reverse-proxy`, `protobuf`, and `dns-spoofing`.

### Common commands

Replace `<tool>` with one of the supported tools and `<id>` with a rule ID from `list` or `get`.

```bash
# Read rules
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> list
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> list --enabled true
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> get <id>

# Change one rule
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> update <id> --name "New name"
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> delete <id>

# Turn a whole tool on or off
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> enable
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> disable

# Turn one rule on or off
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> enable <id>
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> disable <id>
```

`enable <id>` also turns on its tool when needed. Turning off a tool keeps each rule's own enabled setting. Updates change only the fields you send; delete removes the rule right away.

`map-local`, `map-remote`, `breakpoint`, and `scripting` also have a `folders` command to manage rule folders, and their `list` and `create` commands accept `--folder <name or id>`. Run `/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules map-local folders --help` to see the options.

### Create a rule

These are the smallest create commands. Optional flags let you set more fields. Run `/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules <tool> create --help` to see them.

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules block-list create https://ads.example.com/*
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules allow-list create https://api.example.com/*
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules ssl-proxying create '*.example.com' --list include
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules map-local create https://api.example.com/* --path ./response.json
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules map-remote create https://old.example.com/* https://new.example.com/
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules breakpoint create https://api.example.com/* --phase both
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules scripting create https://api.example.com/* --script-file ./rule.js
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules network-condition create --profile 3g
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules reverse-proxy create https://upstream.example.com --local-port 8080
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules protobuf create https://api.example.com/* --request-type package.Request
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules dns-spoofing create example.com 127.0.0.1
```

Common rule flags include `--name`, `--enabled true|false`, `--method`, `--match wildcard|regex`, and `--include-subpaths true|false` when the tool supports them. Names are optional. If you omit an optional value, Proxyman uses that tool's normal default.

### JSON input

For create and update, use `--input <file>` to send a JSON object. Use `--input -` to read JSON from standard input. Do not mix `--input` with field flags.

```bash
printf '%s' '{"url":"https://api.example.com/*","name":"Local API","enabled":true}' \
  | /Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules map-local create --input -

/Applications/Proxyman.app/Contents/MacOS/proxyman-cli rules map-local update <id> --input ./map-local-change.json
```

When Proxyman is closed, the command returns JSON with `ok: false` and the `app_not_running` error code. Input errors use exit code `2`; other errors use exit code `1`.

## 14. Company Policy

### MCP (Proxyman macOS 6.15.0+)

* Enable or disable the [MCP](mcp.md) feature, even when Proxyman is closed
* If MCP is disabled from the command line, users can't enable it again in the Settings

Disable MCP and lock the Settings toggle:

```
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli mcp off
```

Enable MCP and unlock the toggle:

```
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli mcp on
```

## 15. HTTP version

Read or change the global [HTTP/2](basic-features/http2.md) policy. Keep Proxyman open; these commands work even when MCP is disabled.

```bash
# Read the current policy
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli http-version status

# Prefer HTTP/2, with HTTP/1.1 fallback
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli http-version set prefer_http2

# Turn the HTTP/2 preference off
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli http-version set http1_only
```

HTTP/2 is off by default. Changing the policy closes active HTTP, WebSocket, and Server-Sent Events connections and refreshes the Compose client. Setting the current policy again leaves connections open.

The policy does not prove which protocol a request used. Check the captured request and upstream connection. With Network Extension capture, a client offering only `h2` keeps HTTP/2 even under `http1_only`.

Both commands return JSON. Status includes `httpVersionMode` and `http2Enabled`; `set` also includes `previousMode` and `changed`. For example, changing from HTTP/1 to the HTTP/2 preference returns:

```json
{
  "success": true,
  "data": {
    "httpVersionMode": "prefer_http2",
    "http2Enabled": true,
    "previousMode": "http1_only",
    "changed": true
  }
}
```

## 16. Network Extension

Manage [Network Extension](advanced-features/network-extension.md) installation and capture from the command line. Keep Proxyman open; MCP does not need to be enabled.

{% hint style="info" %}
Network Extension requires the direct Proxyman edition and macOS 26 or later. Installation and capture require Proxyman PRO. Status and uninstall remain available without PRO. Setapp does not support Network Extension.
{% endhint %}

```bash
# Read installation and capture status without changing either
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli network-extension status

# Install or update the bundled extension without enabling capture
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli network-extension install

# Enable capture, installing the extension if necessary
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli network-extension enable

# Stop capture and keep the extension installed
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli network-extension disable

# Retry requested installation or capture after resolving an error
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli network-extension retry

# Stop capture and remove the extension and its saved network configurations
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli network-extension uninstall
```

`install` leaves capture off if it is already off. `enable` starts capture and turns the helper-based system proxy off. The system proxy cannot be enabled while Network Extension capture is on.

`disable` and `uninstall` close existing connections through the provider, including direct TCP connections. Afterwards, the system proxy follows **Auto Override System Proxy Settings at Launch**.

macOS may ask for approval or a restart. Complete those steps, then run `network-extension status` again. A successful command means the request was accepted; it does not mean installation or capture has finished. If an operation is busy or times out, read status before repeating it.

HTTPS decryption still requires a trusted Proxyman certificate and matching SSL Proxying rules. Reconnect clients to capture newly opened connections.

### Read the JSON status

| Field | Meaning |
| --- | --- |
| `supported` | Whether this app and macOS version support Network Extension. Unsupported hosts return `false` and reject changes. |
| `installed`, `installedBuild`, `bundledBuild` | Installation reported by macOS and the build bundled with the running app. |
| `systemExtensionEnabled` | Whether macOS reports the installed extension as enabled. |
| `proAvailable` | Whether Proxyman PRO is available for installation and capture. |
| `captureEnabled` | Whether capture has been requested. |
| `captureActive` | Whether the provider has acknowledged the capture session. |
| `state`, `message` | Current app state and a readable explanation. |
| `operationPending` | Whether an installation, removal, or capture startup is in progress. |
| `approvalRequired`, `restartRequired` | Whether approval or a restart is needed. |
| `removalPending` | Whether macOS still has extension records awaiting removal, including after an app relaunch. |
| `systemProxyEnabled` | Whether Proxyman currently reports the macOS system proxy as enabled. |

Supported hosts return these fields under `data`. `disable` does not wait for an installation query, so `installed` is `null` in its response. Use `status` for a fresh installation check.

### JSON output and exit codes

The `http-version` and `network-extension` command groups return a JSON response with `success`, `data` when available, and `error` on failure.

* `0`: The read succeeded or the change was accepted. Check Network Extension status for completion.
* `1`: The command failed, Proxyman is closed, or the command timed out.
* `64`: Invalid command-line arguments. Parser errors and help use plain text.

Check the syntax supported by your installed app with:

```bash
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli http-version --help
/Applications/Proxyman.app/Contents/MacOS/proxyman-cli network-extension --help
```
