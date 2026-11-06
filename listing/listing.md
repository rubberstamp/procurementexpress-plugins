# ProcurementExpress MCP: master listing copy

Single source of truth for every MCP directory submission. Copy fields from here;
`store-fields.md` says which field goes where in each store. Facts were checked
against the code on 2026-11-06 (`app/services/mcp_access/`, `config/initializers/doorkeeper.rb`).
If a tool or scope changes, update this file first.

---

## Identity

| Field | Value |
|---|---|
| Display name | ProcurementExpress |
| Registry / slug name | `procurementexpress` |
| Official registry name | `com.procurementexpress/mcp` |
| Server URL (Streamable HTTP) | `https://app.procurementexpress.com/mcp` |
| Transport | Streamable HTTP (remote, hosted; nothing to install) |
| Authentication | OAuth 2.1 with Dynamic Client Registration (RFC 7591) and PKCE (S256) |
| OAuth discovery | `https://app.procurementexpress.com/.well-known/oauth-protected-resource` |
| Setup guide (docs URL) | `https://app.procurementexpress.com/mcp/setup` |
| Website | `https://procurementexpress.com` |
| Privacy policy | `https://procurementexpress.com/privacy-policy/` |
| Terms | `https://procurementexpress.com/terms-of-service/` |
| Icon (310×310 PNG) | `https://app.procurementexpress.com/ms-icon-310x310.png` |
| Icon (192×192 PNG) | `https://app.procurementexpress.com/android-icon-192x192.png` |
| Logo file (310×310 PNG, in this repo) | `procurementexpress/assets/logo.png` |
| Publisher | ProcurementExpress (RubberStamp.io) |
| Support email | support@procurementexpress.com |
| Repository | `https://github.com/rubberstamp/procurementexpress-plugins` (plugins, listing kit and this file; the server itself is closed source) |
| License | Plugins and listing kit: MIT. Hosted server: proprietary |
| Pricing | Included with a paid ProcurementExpress subscription |
| Version | 1.0.0 |
| MCP protocol version | 2025-11-25 |

> Check before submitting: the support address, and whether the marketing site has a page
> at `https://procurementexpress.com/mcp` you want to use instead of the setup guide.

---

## Taglines

**≤ 60 characters**
> Purchase orders, budgets and invoices for your AI agent

**≤ 100 characters**
> Let your AI assistant check approvals, match invoices to POs, plan budgets and draft purchase orders

**≤ 160 characters (meta description)**
> Connect Claude, ChatGPT, Copilot Studio or Cursor to ProcurementExpress: review approvals, match invoices to POs, plan budgets and draft purchase requests.

---

## Short description (≤ 300 characters)

ProcurementExpress MCP connects your AI assistant to your company's purchasing. Check POs waiting for your approval, match supplier invoices to PO lines, update budgets, send supplier documents in by email and draft purchase requests. Every change is previewed before it is saved.

## Medium description (≤ 750 characters)

The official remote MCP server for ProcurementExpress, the purchase order and spend control software. Connect Claude, ChatGPT, Copilot Studio, Cursor or any MCP client with OAuth, choose the company and permissions, and your assistant can:

- list the purchase orders waiting for your approval
- find invoices with unmatched lines and link them to the right PO lines
- read budgets, and plan single or bulk budget changes from a spreadsheet
- turn a forwarded supplier email (PDF quote or invoice) into a draft PO or invoice
- fill in, check and create purchase requests as drafts

Every write shows a preview and runs only after you approve. The agent has your role and permissions, and can never approve a purchase.

## Long description (README / detail page, Markdown)

```markdown
# ProcurementExpress MCP

The official remote MCP server for [ProcurementExpress](https://procurementexpress.com),
the purchase order, approval and spend control platform for finance teams.

Connect your AI assistant to your company's purchasing data, with the same role and
permissions you have in ProcurementExpress. Nothing to install: add the server URL,
sign in, choose a company and the permissions to grant.

**Server URL:** `https://app.procurementexpress.com/mcp`

## What you can do

- **Approvals:** "What is waiting for my approval?" Lists the purchase orders awaiting
  your approval or delegated approval.
- **Invoice matching:** find invoices with unresolved lines, compare them with candidate
  PO lines (ordered, already billed, received), preview link and unlink decisions, then
  apply them once you approve.
- **Budgets:** get an overview, list and inspect budgets, match spreadsheet rows to
  existing budgets, and preview up to 20 creates or updates at a time. Large setups run
  as one bulk plan with a full before/after review and CSV export.
- **Supplier documents:** get a one-time email address, forward the supplier's email with
  its PDF, and ProcurementExpress scans it into a draft purchase request, an inbox document
  or an invoice, or attaches it to an existing PO.
- **Purchase requests:** see the suppliers, departments, budgets and custom fields you can
  use, validate a request and its budget impact, then create it as a draft (or submit it
  when you explicitly ask).

## Safe by design

- OAuth 2.1 with PKCE. You pick the company and each permission on the consent screen;
  with nothing ticked, access is read-only.
- Every write is a two-step preview → apply, tied to a review digest, so the agent
  cannot change something you have not seen.
- The agent acts as you: your role, departments and approval limits apply. It can never
  approve a purchase order, pay an invoice or bypass the approval flow.
- Access tokens last 15 minutes. Revoke a connection any time in ProcurementExpress.

## Requirements

- A ProcurementExpress user in an active, paid company.
- MCP access turned on for the company by a company admin
  (Integrations › MCP in ProcurementExpress).

## Setup

Full guide: https://app.procurementexpress.com/mcp/setup

**Claude** (web, Desktop, mobile): Settings › Connectors › Add custom connector › paste the URL.
**ChatGPT:** add a custom connector (developer mode), paste the URL, choose OAuth.
**Microsoft Copilot Studio:** Agent › Tools › Add › Model Context Protocol › paste the URL,
OAuth 2.0, Dynamic (with discovery).
**Cursor / VS Code / any client:**

    {
      "mcpServers": {
        "procurementexpress": { "url": "https://app.procurementexpress.com/mcp" }
      }
    }

## Permissions (OAuth scopes)

| Scope | Grants |
|---|---|
| `procurement:read` | Company context, approvals queue, budgets (read) |
| `budgets:write` | Create and update budgets after review |
| `invoices:read` | Read invoices and their matching context |
| `invoices:match` | Link and unlink invoice lines to PO lines after review |
| `documents:write` | Send supplier documents in by email |
| `purchase_orders:write` | Create purchase requests (draft by default) |

## Support

support@procurementexpress.com · https://procurementexpress.com
```

---

## Categories and tags

Pick the closest category each store offers, in this order:

1. Finance / Accounting
2. Business / Productivity
3. Enterprise / ERP
4. Data & Analytics

**Tags (use as many as the store allows, in this order):**
`procurement`, `purchase-orders`, `invoices`, `accounts-payable`, `budgets`, `approvals`,
`spend-management`, `finance`, `three-way-matching`, `purchasing`, `oauth`, `remote`, `saas`

**Keywords (comma-separated form fields):**
procurement, purchase orders, PO approval, invoice matching, accounts payable, AP automation,
budgets, budget planning, spend control, purchase requests, supplier invoices, finance

---

## Tools (27)

Tools appear only when the connection has the scope listed and the user's role allows it (budget
drafting tools need a role that can create budgets). Nothing is saved without a preview the user approved.

| Tool | What it does | Scope |
|---|---|---|
| `get_context` | Identify the connected company and available capabilities | read |
| `list_pending_approvals` | Purchase orders awaiting your (or delegated) approval | read |
| `get_budget_overview` | Start of budget work: summaries, totals by currency, distributions | read |
| `list_budgets` | List budgets with cost codes, dates, allocations and spending | read |
| `get_budget` | Inspect one budget | read |
| `get_budget_setup_options` | Company currency, departments and supported budget fields | read |
| `match_budget_rows` | Resolve up to 20 spreadsheet rows to existing budgets | read |
| `preview_budget_changes` | Preview up to 20 budget creates/updates; changes nothing | read + budget-manager role |
| `get_bulk_budget_plan` | Progress, totals, review digest and CSV export of a bulk plan | read + budget-manager role |
| `list_bulk_budget_plan_items` | Paginated before/after detail of a bulk plan | read + budget-manager role |
| `apply_budget_changes` | Apply a reviewed budget preview after approval | budgets:write |
| `create_bulk_budget_plan` | Start one logical bulk budget setup | read + budget-manager role |
| `append_bulk_budget_changes` | Stage 1–20 CSV rows into a draft plan | read + budget-manager role |
| `prepare_bulk_budget_plan` | Seal the plan and build the full preview | read + budget-manager role |
| `cancel_bulk_budget_plan` | Stop unstarted work in a bulk plan | read + budget-manager role |
| `apply_bulk_budget_plan` | Apply a prepared plan after approval | budgets:write |
| `set_budget_conventions` | Save confirmed company budget conventions | budgets:write |
| `list_invoices_needing_matching` | Invoices with unresolved lines | invoices:read |
| `get_invoice_matching_context` | Invoice lines, links, suggestions, PO lines, billing and receipts | invoices:read |
| `find_invoice_order_candidates` | Same-supplier candidate POs by reference or description | invoices:read |
| `preview_invoice_matches` | Preview up to 50 link/unlink decisions | invoices:match |
| `apply_invoice_matches` | Apply the reviewed matches after approval | invoices:match |
| `request_document_drop` | One-time email address for a supplier document | documents:write |
| `get_document_drop` | Status and created records of a document drop | documents:write |
| `get_purchase_request_options` | Suppliers, departments, budgets, custom fields, tax rates, currencies | purchase_orders:write |
| `preview_purchase_request` | Validate a request and show its budget impact | purchase_orders:write |
| `create_purchase_request` | Create the request as a draft (or submit on request) | purchase_orders:write |

---

## Example prompts

1. What purchase orders are waiting for my approval?
2. List my invoices that still have lines not matched to a purchase order.
3. Match invoice INV-1042 to its purchase order and show me the preview first.
4. How much is left on the Marketing budget this year?
5. Here is our FY2027 budget spreadsheet: create the budgets that don't exist yet.
6. I'm forwarding a supplier quote; turn it into a draft purchase request.
7. Raise a purchase request for 10 laptops from Dell for the IT department.

---

## FAQ (for stores with a FAQ field)

**Is it free?** The MCP server is included with a paid ProcurementExpress subscription.

**Do I need to install anything?** No. It is a hosted server; add the URL in your MCP client.

**Can the AI approve purchases or pay invoices?** No. It can preview and, with your approval,
save changes, but approvals and payments stay in ProcurementExpress.

**Which AI apps work?** Any client that supports remote MCP servers with OAuth: Claude,
ChatGPT, Microsoft Copilot Studio, Cursor and VS Code / GitHub Copilot.

**How do I revoke access?** In ProcurementExpress, open your MCP connections and disconnect,
or a company admin turns MCP off for the company.

---

## Client config snippets

**Generic `mcp.json` / Claude Desktop / Cursor**

```json
{
  "mcpServers": {
    "procurementexpress": {
      "url": "https://app.procurementexpress.com/mcp"
    }
  }
}
```

**VS Code (`.vscode/mcp.json`)**

```json
{
  "servers": {
    "procurementexpress": {
      "type": "http",
      "url": "https://app.procurementexpress.com/mcp"
    }
  }
}
```

**Clients that only speak stdio** (bridge with `mcp-remote`)

```json
{
  "mcpServers": {
    "procurementexpress": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://app.procurementexpress.com/mcp"]
    }
  }
}
```

**Claude Code**

```bash
claude mcp add --transport http procurementexpress https://app.procurementexpress.com/mcp
```
