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

## Layout

- `.claude-plugin/marketplace.json`: the Claude Code marketplace
- `.cursor-plugin/marketplace.json`: the Cursor marketplace
- `.agents/plugins/marketplace.json`: the Codex marketplace
- `<plugin>/.claude-plugin/plugin.json`, `<plugin>/.cursor-plugin/plugin.json` and `<plugin>/.codex-plugin/plugin.json`: one manifest per tool, all sharing the plugin's `mcp.json`

To add a plugin, create a sibling folder with all three manifests and list it in all three marketplace files.
