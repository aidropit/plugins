# aidrop.it plugins

Official plugin marketplace for [**aidrop.it**](https://aidrop.it) — *your agent builds, we run it*. Your coding agent writes the code; aidrop.it keeps the repository, builds it, runs it at a public address and gives it a database, a cache or a queue when it needs one — all driven from the conversation over MCP.

---

# How to install

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

Inside Claude Code, run `/mcp`, pick `aidropit`, and complete the browser sign-in.*

## Codex

```bash
codex plugin marketplace add aidropit/plugins --sparse .agents/plugins
codex plugin add aidropit@aidropit
```

OAuth runs on install — complete sign-in in the browser if prompted, or run `codex mcp login aidropit`.

## Anything else that speaks MCP (Cursor, …)

Point the client at the same address and approve the consent screen it opens on the first call:

```json
{
  "mcpServers": {
    "aidropit": {
      "url": "https://mcp.aidrop.it/mcp"
    }
  }
}
```

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
