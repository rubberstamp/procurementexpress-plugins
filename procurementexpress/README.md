# ProcurementExpress

Connects your agent to [ProcurementExpress](https://www.procurementexpress.com) through its remote MCP server, `https://app.procurementexpress.com/mcp`.

## Before you start

MCP access is switched on per company. If your company does not appear on the consent screen, ask ProcurementExpress support to enable MCP for it. A company admin can review and disconnect connected apps under **Integrations → MCP** in ProcurementExpress.

## Connecting

The first tool call opens a ProcurementExpress sign-in and consent screen (OAuth). You pick the company and the permissions to grant. Read access is always included; every other permission is optional:

| Permission | Lets the agent |
| --- | --- |
| `procurement:read` | see your company context and the purchase orders waiting for your approval |
| `budgets:write` | preview and apply budget changes, including bulk budget plans |
| `invoices:read` / `invoices:match` | find invoices that need matching and link them to purchase orders |
| `purchase_orders:write` | preview and create purchase requests |
| `documents:write` | get a one-time email address for forwarding a supplier document in |

Everything the agent does runs as you, with your ProcurementExpress role and permissions. Budget changes, invoice matches and purchase requests are previewed before they are applied.

## Install

**Claude Code**

```
/plugin marketplace add rubberstamp/procurementexpress-plugins
/plugin install procurementexpress@procurementexpress
```

**Cursor**: install **ProcurementExpress** from the Cursor Marketplace.
