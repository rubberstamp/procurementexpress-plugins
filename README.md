# ProcurementExpress plugins

Official [ProcurementExpress](https://www.procurementexpress.com) plugins for Claude Code, Cursor and Codex.

| Plugin | What it does |
| --- | --- |
| [`procurementexpress`](procurementexpress/) | Connects your agent to the ProcurementExpress MCP server: approvals, budgets, purchase requests, supplier documents and invoice matching. |

## Install in Claude Code

```
/plugin marketplace add rubberstamp/procurementexpress-plugins
/plugin install procurementexpress@procurementexpress
```

## Use the MCP server directly

Any MCP client that supports remote servers with OAuth can connect without a plugin.

**Server URL:** `https://app.procurementexpress.com/mcp` (Streamable HTTP, OAuth 2.1 with dynamic client registration)

```json
{
  "mcpServers": {
    "procurementexpress": { "url": "https://app.procurementexpress.com/mcp" }
  }
}
```

Claude Code: `claude mcp add --transport http procurementexpress https://app.procurementexpress.com/mcp`

On first use you sign in to ProcurementExpress, pick the company and choose the permissions to
grant. With none ticked, access is read-only. Every change is previewed before it is saved, and the
agent can never approve a purchase order or pay an invoice. MCP access is switched on per company
by a company admin. Permissions, tools and setup for Claude, ChatGPT, Microsoft Copilot Studio,
Cursor and VS Code: [`procurementexpress/README.md`](procurementexpress/README.md) and
[`listing/listing.md`](listing/listing.md).

## Layout

- `.claude-plugin/marketplace.json`: the Claude Code marketplace
- `.cursor-plugin/marketplace.json`: the Cursor marketplace
- `.agents/plugins/marketplace.json`: the Codex marketplace
- `<plugin>/.claude-plugin/plugin.json`, `<plugin>/.cursor-plugin/plugin.json` and `<plugin>/.codex-plugin/plugin.json`: one manifest per tool, all sharing the plugin's `mcp.json`

- `listing/`: copy and manifests for MCP directories (Official MCP Registry `server.json`, Docker, ToolSDK, LobeHub, per-store form fields)

To add a plugin, create a sibling folder with all three manifests and list it in all three marketplace files.
