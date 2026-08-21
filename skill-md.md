---
description: >-
  Official agent skills Proxyman for inspecting, replaying, and debugging HTTP,
  HTTPS, WebSocket, and app traffic.
---

# SKILL.md

## Proxyman Agent Skills

Official agent skills for [Proxyman](https://proxyman.com), a web debugging proxy for inspecting, replaying, and debugging HTTP, HTTPS, WebSocket, device, and application traffic.

The bundle covers installation, every macOS App Settings tab, certificate lifecycle and recovery, MCP connection and all current MCP operations, live documentation lookup, debugging-tool workflows, licensing, `proxyman-cli`, and HTTPS capture across devices and runtimes. Proxyman MCP controls a running local app through its bundled stdio bridge; it is not a cloud API.

See coverage and maintenance evidence for the requirement-by-requirement audit.

* Github Repo: [https://github.com/ProxymanApp/proxyman-SKILL.md](https://github.com/ProxymanApp/proxyman-SKILL.md)

### Plugin

* ✅ Install Proxyman Plugin at [OpenAI Marketplace](https://chatgpt.com/plugins/plugins_6a88afab118c8191970bbc714223ff14).

### Installation

Install all skills:

```bash
npx skills add ProxymanApp/proxyman-SKILL.md/skills
```

Install one skill:

```bash
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-download-setup
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-app-settings
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-certificates-recovery
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-mcp-setup
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-traffic-debugging
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-debugging-tools
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-license-management
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-cli
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-https-capture
```

For manual installation, clone the repository and copy the desired folders under `skills/` into the agent's skills directory:

```bash
git clone https://github.com/ProxymanApp/proxyman-SKILL.md.git
```

Restart or reload the agent afterward.

| Agent                      | Skills directory     |
| -------------------------- | -------------------- |
| OpenAI Codex CLI           | `~/.codex/skills/`   |
| Claude Code/Desktop        | `~/.claude/skills/`  |
| Cursor                     | `~/.cursor/skills/`  |
| GitHub Copilot CLI/VS Code | `~/.copilot/skills/` |

### Skills

| Skill                            | Use it for                                                                                                                                                                                              |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `proxyman-download-setup`        | Download, install, launch, and prepare Proxyman on macOS, Windows, or Linux.                                                                                                                            |
| `proxyman-app-settings`          | Audit, explain, and safely change every current macOS Settings tab, including build/license limitations and GUI-only boundaries.                                                                        |
| `proxyman-certificates-recovery` | Install/trust generated or custom roots, manage custom server/client identities, capture diagnostics, and safely use Help-menu recovery actions including Factory Reset.                                |
| `proxyman-mcp-setup`             | Connect an agent to the bundled stdio MCP bridge and troubleshoot handshake/tool discovery.                                                                                                             |
| `proxyman-traffic-debugging`     | Inspect traffic and operate the complete current MCP surface: all 70 reviewed actions, resources, and prompts.                                                                                          |
| `proxyman-debugging-tools`       | Fetch current official docs and deeply guide Breakpoint, Map Local/Remote, Scripting, Compose/Repeat, Protobuf, Network Conditions, Reverse Proxy, and TLS Key Logging with exact interface boundaries. |
| `proxyman-license-management`    | Activate/unlink the current device and manage remote devices, seats, transfers, and renewal safely.                                                                                                     |
| `proxyman-cli`                   | Discover installed CLI syntax and automate proxy, MCP, configuration, logs, certificates, and rules.                                                                                                    |
| `proxyman-https-capture`         | Configure and verify HTTPS capture for devices/runtimes/containers and choose or integrate Atlantis for controlled apps.                                                                                |

### Routing

* Proxyman is absent: `proxyman-download-setup`.
* The user asks where an App Setting lives, what it changes, why it is locked, or wants a Settings audit/change: `proxyman-app-settings`.
* The user needs generated/custom root trust, custom server/client certificates, Debug Mode, Reset Network Proxy, or Factory Reset: `proxyman-certificates-recovery`.
* Proxyman is installed but MCP tools are missing: `proxyman-mcp-setup`.
* The user wants the agent to inspect/change Proxyman through MCP: `proxyman-traffic-debugging`.
* The user asks how a Proxyman tool works or needs the latest official guide: `proxyman-debugging-tools`.
* The user needs license activation, unlink, remote revoke, or License Manager: `proxyman-license-management`.
* The user wants a shell command or scripted operation: `proxyman-cli`.
* The user needs traffic from a device, emulator, app, runtime, or container to appear and decrypt: `proxyman-https-capture`.

Skills can work together. For example, use HTTPS Capture to configure an Android emulator, then Traffic Debugging to verify its flows and create a Map Local rule.

### Requirements And Safety

* Proxyman must be installed and running before operational MCP tools work.
* Enable Settings > MCP > MCP Server, or use the installed `proxyman-cli mcp` hierarchy after reading version-matched help.
* Configure agents with Proxyman's bundled stdio bridge, not a fixed HTTP URL or the main app executable.
* Treat live `tools/list`, resources/prompts discovery, and installed CLI help as authoritative for schemas and syntax.
* Treat the installed Settings UI as authoritative for preferences; the reviewed MCP server is not a generic App Settings API.
* Treat certificate/private-key imports, trust changes, Debug Mode output, and Factory Reset as sensitive; preserve required sources and backups outside Proxyman-managed folders before destructive recovery.
* Keep **Redact Sensitive Data Before Sending to AI** enabled unless raw data is explicitly required and approved.
* MCP preview redaction does not sanitize original HAR/Proxyman log exports.
* Fetch `https://docs.proxyman.com/llms.txt` and its linked Markdown pages when current product behavior matters.
* License keys, TLS session-key logs, portal access links, proxy credentials, certificate passwords, and captured secrets must not be stored in skills, commands, logs, or reports.

### Plugin Packaging

This directory is a self-contained skill bundle and can be placed under a Codex plugin's `skills/` directory. The plugin still needs to configure or document the local Proxyman MCP bridge separately; packaging these skills does not embed the Proxyman app, bridge executable, license, or a running MCP connection.

The production Proxyman plugin is available on [ChatGPT](https://chatgpt.com/plugins/plugins_6a88afab118c8191970bbc714223ff14).

The publishable plugin source is available at `plugins/proxyman`. It is a skills-only package with a public-ready manifest and Proxyman brand asset. See `SUBMISSION.md` for the marketplace listing, starter prompts, reviewer tests, release notes, and the remaining OpenAI Platform submission checks.
