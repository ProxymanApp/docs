---
description: Explain how to use MCP on Proxyman with Cursor or Claude Code
---

# MCP

## 1. What is Proxyman MCP?

**Proxyman MCP** (Model Context Protocol) is a feature that enables AI assistants (Claude, Cursor, and other MCP-compatible tools) to directly interact with the Proxyman macOS app. It allows AI to inspect HTTP traffic, create debugging rules, and control Proxyman - all through natural language conversations.

The architecture consists of two components:

* **MCP HTTP Server** - Runs inside Proxyman app on localhost with token-based authentication
* **MCP CLI Server** - A stdio-based MCP server that AI tools connect to, which forwards commands to Proxyman

## 2. Benefits

| Benefit                      | Description                                                                          |
| ---------------------------- | ------------------------------------------------------------------------------------ |
| **AI-Powered Debugging**     | Ask AI to analyze captured traffic, find specific requests, or explain API responses |
| **Hands-Free Rule Creation** | Create breakpoints, map local/remote rules through conversation                      |
| **Faster Workflow**          | Export cURL commands, filter flows, and manage sessions without switching context    |
| **Secure by Design**         | Localhost-only server with per-session token authentication                          |
| **IDE Integration**          | Works seamlessly with Cursor and other MCP-compatible tools                          |

## 3. How to Use

#### Setup

1. **Enable MCP in Proxyman**
   * Open Proxyman → Settings → MCP
   * Toggle **Enable MCP Server**
2.  **Configure your MCP client** (e.g., Cursor, Claude Desktop)

    Add to your MCP configuration:

* Production Version:

```json
{
  "mcpServers": {
    "proxyman": {
      "command": "/Applications/Proxyman.app/Contents/MacOS/mcp-server"
    }
  }
}
```

* Setapp Version

```json
{
  "mcpServers": {
    "proxyman": {
      "command": "/Applications/Setapp/Proxyman.app/Contents/MacOS/mcp-server"
    }
  }
}
```

3. **Start using**

* Ensure Proxyman is running
* Ask your AI assistant to interact with Proxyman

#### Example Prompts

```
"Show me the last 10 API requests to api.example.com"
"Create a breakpoint for all POST requests to /api/users"
"Export the failed request as a cURL command"
"Enable SSL proxying for *.stripe.com"
```

### 4. Available Tools

#### Read-Only Tools

| Tool                     | Description                                                                                                      |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| `get_version`            | Returns Proxyman version and build number                                                                        |
| `get_proxy_status`       | Returns recording state, proxy port, and SSL proxying status                                                     |
| `get_flows`              | Lists captured HTTP/HTTPS flows with optional filters (`limit`, `host_filter`, `method_filter`, `status_filter`) |
| `get_flow_detail`        | Returns full details of a specific flow including headers, body preview, query params, and cookies               |
| `list_rules`             | Lists all debugging rules (breakpoints, map local, map remote, blacklist)                                        |
| `get_ssl_proxying_list`  | Returns SSL proxying include/exclude domain lists                                                                |
| `get_certificate_status` | Returns root certificate installation status                                                                     |

#### Write Tools

| Tool                  | Description                                             | Required Params      |
| --------------------- | ------------------------------------------------------- | -------------------- |
| `create_breakpoint`   | Creates a breakpoint to pause/inspect matching requests | `url` (pattern)      |
| `create_map_local`    | Returns custom responses for matching URLs              | `url` (pattern)      |
| `create_map_remote`   | Redirects requests from one URL to another              | `from_url`, `to_url` |
| `create_blacklist`    | Blocks requests matching a URL pattern                  | `url` (pattern)      |
| `enable_ssl_proxying` | Enables HTTPS decryption for a domain                   | `domain`             |

#### Session Control

| Tool               | Description                                    |
| ------------------ | ---------------------------------------------- |
| `clear_session`    | Clears all captured flows from current session |
| `toggle_recording` | Starts or stops traffic recording              |

#### Flow Operations

| Tool               | Description                                                                                                         |
| ------------------ | ------------------------------------------------------------------------------------------------------------------- |
| `export_flow_curl` | Exports a captured request as a runnable cURL command                                                               |
| `filter_flows`     | Advanced filtering with multiple criteria (url, host, method, status, headers, body) supporting AND/OR combinations |

#### App Control

| Tool            | Description                      |
| --------------- | -------------------------------- |
| `open_proxyman` | Launches Proxyman if not running |
| `quit_proxyman` | Quits the Proxyman app           |

***

### Security

* Server binds to `127.0.0.1` only (no network exposure)
* Per-session cryptographic token stored in `~/Library/Application Support/com.proxyman.NSProxy/mcp-handshake.json`
* Handshake file has `0600` permissions (owner-only access)
* Sensitive data (auth tokens, passwords, API keys) is automatically redacted in responses
