# aidrop.it plugins

Official plugin marketplace for [**aidrop.it**](https://aidrop.it) — portable memory for AI tools. The same memory in every tool that speaks MCP, captured as you work.

The **`aidrop-memory`** plugin bundles, in one install:

- the **aidrop.it remote MCP server** (`https://mcp.aidrop.it/mcp`, OAuth — no token to paste), and
- the **memory-usage skill** that teaches the agent when to read and write your memory.

This repo hosts marketplaces for both **Claude Code** and **Codex**.

---

## Claude Code

```text
/plugin marketplace add aidropit/plugins
/plugin install aidrop-memory@aidrop
```

Then authenticate the MCP server (one-time OAuth):

```text
/mcp
```

Pick `aidrop` and complete the browser sign-in. Memory tools (`memory_search`, `memory_write`, …) and the `aidrop-memory` skill are now available.

## Codex

```bash
codex plugin marketplace add aidropit/plugins --sparse .agents/plugins
codex plugin add aidrop-memory@aidrop
```

OAuth runs on install — complete sign-in in the browser if prompted, or run `codex mcp login aidrop`.

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
└── skills/aidrop-memory/SKILL.md    Memory-usage skill (shared)
```

The MCP server is a **public OAuth client** with Dynamic Client Registration — no
client secret or static token is stored in this repo.

## Other clients

aidrop.it works with any MCP-aware client (Cursor, Kiro, Gemini CLI, OpenClaw,
Claude, ChatGPT, and more). See the connection guides at
**https://aidrop.it/install**.

## Links

- Website — https://aidrop.it
- MCP endpoint — `https://mcp.aidrop.it/mcp`
- Support — info@aidrop.it
