---
description: >-
  Official agent skills Proxyman for inspecting, replaying, and debugging HTTP,
  HTTPS, WebSocket, and app traffic.
---

# SKILL.md

## Proxyman Agent Skills

Official agent skills for [Proxyman](https://proxyman.com), a web debugging proxy for inspecting, replaying, and debugging HTTP, HTTPS, WebSocket, and app traffic.

These skills help AI coding agents install Proxyman, connect to Proxyman MCP, and use Proxyman's MCP tools correctly. Proxyman MCP controls a running local Proxyman app; it is not a cloud API.

✅ GitHub Repo: [https://github.com/ProxymanApp/proxyman-SKILL.md](https://github.com/ProxymanApp/proxyman-SKILL.md)

### Installation

#### Quick install with skills.sh

Install all Proxyman skills:

```bash
npx skills add ProxymanApp/proxyman-SKILL.md/skills
```

Install one skill:

```bash
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-download-setup
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-mcp-setup
npx skills add ProxymanApp/proxyman-SKILL.md --skill proxyman-traffic-debugging
```

#### Manual setup

Clone this repository:

```bash
git clone https://github.com/ProxymanApp/proxyman-SKILL.md.git
```

Then copy the folders under `skills/` into your agent's skills directory.g

| Agent                     | Skills directory     |
| ------------------------- | -------------------- |
| OpenAI Codex CLI          | `~/.codex/skills/`   |
| Claude Code               | `~/.claude/skills/`  |
| Claude Desktop            | `~/.claude/skills/`  |
| Cursor                    | `~/.cursor/skills/`  |
| GitHub Copilot CLI        | `~/.copilot/skills/` |
| GitHub Copilot in VS Code | `~/.copilot/skills/` |

Example:

```bash
mkdir -p ~/.codex/skills
cp -R skills/* ~/.codex/skills/
```

Each skill folder must contain its `SKILL.md` file. Restart or reload your agent after copying the files.

### Skills

| Skill                        | Description                                                                                                                                              |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `proxyman-download-setup`    | Download, install, launch, and prepare Proxyman on macOS, Windows, or Linux.                                                                             |
| `proxyman-mcp-setup`         | Connect your coding agent to Proxyman MCP using the bundled stdio bridge.                                                                                |
| `proxyman-traffic-debugging` | Use Proxyman MCP for traffic debugging and full MCP operations: flows, rules, Compose, WebSocket, certificates, setup guidance, exports, and automation. |

### Which skill should I use?

* Use `proxyman-download-setup` if Proxyman is not installed yet.
* Use `proxyman-mcp-setup` if Proxyman is installed but your agent cannot see Proxyman MCP tools.
* Use `proxyman-traffic-debugging` after MCP is connected and you want your agent to inspect traffic, diagnose missing capture, create rules, replay requests, or operate Proxyman through MCP.

### Requirements

* Proxyman must be installed and running before MCP tools can work.
* In Proxyman, open Settings > MCP and enable MCP Server.
* MCP uses Proxyman's bundled stdio bridge, not a cloud API or a fixed HTTP URL.
* On Windows, the bridge is normally `mcp-server.exe` beside `Proxyman.exe`; on Linux AppImage builds, launch Proxyman once so it can prepare `${XDG_CONFIG_HOME:-$HOME/.config}/Proxyman/bin/mcp-server`.
* Keep "Redact Sensitive Data Before Sending to AI" enabled unless you explicitly need raw secrets in MCP output.
