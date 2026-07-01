# aidrop.it plugins

Official plugin marketplace + skill for [**aidrop.it**](https://aidrop.it) — portable memory for AI tools. The same memory in every tool that speaks MCP, captured as you work.

The **`aidrop-memory`** plugin bundles, in one install:

- the **aidrop.it remote MCP server** (`https://mcp.aidrop.it/mcp`, OAuth — no token to paste), and
- the **memory skill** that teaches the agent when to read and write your memory.

This repo hosts marketplaces for both **Claude Code** and **Codex**, and the standalone **`SKILL.md`** that any Agent-Skills-compatible tool can use.

---

## Claude Code

In your terminal:

```bash
claude plugin marketplace add aidropit/plugins
claude plugin install aidrop-memory@aidrop
```

Then start Claude Code and authenticate the MCP server (one-time OAuth):

```bash
claude
```

Inside Claude Code, run `/mcp`, pick `aidrop`, and complete the browser sign-in. Memory tools (`memory_search`, `memory_write`, …) and the `aidrop-memory` skill are now available.

## Codex

```bash
codex plugin marketplace add aidropit/plugins --sparse .agents/plugins
codex plugin add aidrop-memory@aidrop
```

OAuth runs on install — complete sign-in in the browser if prompted, or run `codex mcp login aidrop`.

## Standalone skill (Cursor, Kiro, Gemini CLI, OpenClaw, Replit, Lovable, Figma Make, …)

`SKILL.md` follows the open [Agent Skills](https://agentskills.io) standard, so it works in any compatible tool once you've connected the MCP server. Drop it into the tool's skills folder, e.g.:

- Cursor — `.cursor/skills/aidrop-memory/SKILL.md`
- Kiro — `~/.kiro/skills/aidrop-memory/SKILL.md`
- Gemini CLI — `~/.gemini/skills/aidrop-memory/SKILL.md`
- OpenClaw — `~/.openclaw/skills/aidrop-memory/SKILL.md`
- Replit — `.agents/skills/aidrop-memory/SKILL.md`

**Lovable** imports it straight from GitHub (`Settings → Skills → Add → Import from GitHub`):

```
https://github.com/aidropit/plugins/tree/main/plugins/aidrop-memory/skills/aidrop-memory
```

**Figma Make** — prompt box → `Skills → Add skill` → upload the `SKILL.md`.

Full per-tool connection guides: **https://aidrop.it/install**.

---

## What's inside

```
.claude-plugin/marketplace.json      Claude Code marketplace catalog
.agents/plugins/marketplace.json     Codex marketplace catalog
plugins/aidrop-memory/
├── .claude-plugin/plugin.json       Claude Code manifest
├── .codex-plugin/plugin.json        Codex manifest
├── .mcp.json                        MCP server (Claude Code schema)
├── codex.mcp.json                   MCP server (Codex schema)
└── skills/aidrop-memory/SKILL.md    Memory skill (single source)
```

The MCP server is a **public OAuth client** with Dynamic Client Registration — no client secret or static token is stored in this repo.

## Links

- Website — https://aidrop.it
- MCP endpoint — `https://mcp.aidrop.it/mcp`
- Support — info@aidrop.it
