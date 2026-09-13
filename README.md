# aidrop.it plugins

Official plugin marketplace for [**aidrop.it**](https://aidrop.it) — *your agent builds, we run it*. Your coding agent writes the code; aidrop.it keeps the repository, builds it, runs it at a public address and gives it a database, a cache or a queue when it needs one — all driven from the conversation over MCP.

The **`aidropit`** plugin is one thing: the **aidrop.it remote MCP server** (`https://mcp.aidrop.it/mcp`, OAuth — no token to paste). There is no skill to install: the server's tool descriptions carry what the agent needs.

This repo hosts marketplaces for both **Claude Code** and **Codex**.

> **Upgrading from `aidrop-memory`?** That plugin connected to the retired memory product and no longer works. Uninstall it (`claude plugin uninstall aidrop-memory@aidrop` / `codex plugin remove aidrop-memory@aidrop`) and install `aidropit` as below. The MCP server address is unchanged; an existing OAuth connection is reused.

---

## Claude Code

In your terminal:

```bash
claude plugin marketplace add aidropit/plugins
claude plugin install aidropit@aidropit
```

Then start Claude Code and authenticate the MCP server (one-time OAuth):

```bash
claude
```

Inside Claude Code, run `/mcp`, pick `aidropit`, and complete the browser sign-in. You approve one Project with `service:read` and `service:write` over it. The deploy tools (`service_build`, `service_get`, `shared_resource_create`, …) are now available — open a repository and say *"Deploy this to aidrop.it."*

## Codex

```bash
codex plugin marketplace add aidropit/plugins --sparse .agents/plugins
codex plugin add aidropit@aidropit
```

OAuth runs on install — complete sign-in in the browser if prompted, or run `codex mcp login aidropit`.

## Anything else that speaks MCP (Cursor, Claude, ChatGPT, VS Code, …)

Point the client at the same address and approve the consent screen it opens on the first call:

```json
{ "mcpServers": { "aidropit": { "url": "https://mcp.aidrop.it/mcp" } } }
```

A client with no local shell and git (Claude web, ChatGPT) can read, build and operate what is already in a repository, but cannot put code in — that part needs Claude Code, Codex or Cursor.

Full per-tool connection guides: **https://aidrop.it/install** · docs: **https://docs.aidrop.it/mcp**.

---

## What's inside

```
.claude-plugin/marketplace.json      Claude Code marketplace catalog
.agents/plugins/marketplace.json     Codex marketplace catalog
plugins/aidropit/
├── .claude-plugin/plugin.json       Claude Code manifest
├── .codex-plugin/plugin.json        Codex manifest
├── .mcp.json                        MCP server (Claude Code schema)
└── codex.mcp.json                   MCP server (Codex schema)
```

The MCP server is a **public OAuth client** with Dynamic Client Registration — no client secret or static token is stored in this repo. Access is per Project and revoked from **Management → Connected apps** in the dashboard.

## Links

- Website — https://aidrop.it
- Docs — https://docs.aidrop.it
- MCP endpoint — `https://mcp.aidrop.it/mcp`
- Support — info@aidrop.it
