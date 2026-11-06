# Per-store copy-paste sheet

Field names are quoted exactly as each store shows them (checked 2026-11-06). Values come
from `listing.md`; when a store has a length limit, the value below already fits it.

Common values used below:

- **URL:** `https://app.procurementexpress.com/mcp`
- **Docs:** `https://app.procurementexpress.com/mcp/setup`
- **Icon:** `https://app.procurementexpress.com/ms-icon-310x310.png`
- **Registry name:** `com.procurementexpress/mcp`
- **Repository:** `https://github.com/rubberstamp/procurementexpress-plugins`

---

## 1. Official MCP Registry (do this first)

**How:** the `mcp-publisher` CLI with `server.json`. Steps are in `README.md`. MCPfinder, PulseMCP
(once it reopens) and Glama connectors all read from this registry.

---

## 2. Glama

**How:** glama.ai/mcp/connectors › "Add Server" (needs a Glama account). It likely picks us up
from the Official Registry; check after publishing there and **"Claim ownership"** instead.

- Name: `ProcurementExpress`
- URL: the server URL
- Description: the short description in `listing.md`

UNVERIFIED: the form behind "Add Server", and the claim file path (`/.well-known/glama.json` per one source).

---

## 3. Smithery: **closed**

Self-service publishing ended 31 Oct 2026. Only a curated list remains. Ask: ani [at] smithery [dot] ai.

---

## 4. MCP.so

**How:** https://mcp.so/submit?type=remote-server (Free path goes through review; $39 skips it.)

| Field | Value |
|---|---|
| Remote endpoint URL | `https://app.procurementexpress.com/mcp` |
| Name | `ProcurementExpress` |

---

## 5. PulseMCP: **paused**

Submissions are paused. It will import from the Official Registry when it reopens.

---

## 6. MCPfinder

Nothing to submit. It copies the Official Registry and Glama.

---

## 7. MCP Servers (mcpservers.org)

**How:** https://mcpservers.org/submit (Free: review within 2 weeks; Premium $39: 24 hours.)

| Field | Value |
|---|---|
| Server Name | `ProcurementExpress` |
| Category | `finance` |
| Short Description | Connect your AI assistant to ProcurementExpress: approvals, invoice-to-PO matching, budgets and purchase requests, with a preview before every change. |
| Repository, Website or Documentation | `https://github.com/rubberstamp/procurementexpress-plugins` |
| Official MCP Registry Name | `com.procurementexpress/mcp` |
| This server supports remote connections | ✓ |
| Contact Email | *(the team inbox)* |

---

## 8. AIbase MCP

No submission route found. Contact AIbase directly if wanted.

---

## 9. Docker MCP Catalog

**How:** pull request to `docker/mcp-registry`. Copy `docker/procurementexpress/` from this folder to
`servers/procurementexpress/` in a fork (or run `task remote-wizard` and answer with the values below).

| Wizard question | Answer |
|---|---|
| Server Name | `procurementexpress` |
| Category | `finance` |
| Server Title | `ProcurementExpress` |
| Description | Purchase orders, approvals, invoice-to-PO matching, budgets and purchase requests from ProcurementExpress, with a preview before every change. |
| Icon URL | the icon URL |
| Documentation URL | the docs URL |
| Transport Type | `streamable-http` |
| Server URL | the server URL |
| Use OAuth? | Yes |

Test before opening the PR:

```bash
task catalog -- procurementexpress
docker mcp catalog import $PWD/catalogs/procurementexpress/catalog.yaml
docker mcp server enable procurementexpress
docker mcp oauth authorize procurementexpress
```

UNVERIFIED: whether Docker's OAuth flow works with our Dynamic Client Registration. The test
above answers it; if `oauth authorize` fails, do not open the PR.

---

## 10. LobeHub

**How:** `lhm` CLI (Node 22+), run from this folder. `lobehub/lhm.plugin.json` is ready. The publish
command needs a GitHub repo the connected account can push to, and the listing's README comes from
it: this repo, whose root README carries the MCP section.

```bash
npx -y @lobehub/market-cli login
npx -y @lobehub/market-cli github connect
npx -y @lobehub/market-cli plugin publish https://github.com/rubberstamp/procurementexpress-plugins --dir "$PWD/lobehub"
```

---

## 11. MCP Market

**How:** https://mcpmarket.com/submit › "MCP Server" › Source **"Remote MCP"** ($69 one-time, listed within 24 hours).

| Field | Value |
|---|---|
| Server name * | `ProcurementExpress` |
| MCP endpoint URL * | `https://app.procurementexpress.com/mcp` |
| Short description * (≤200) | Connect your AI assistant to ProcurementExpress: approvals, invoice-to-PO matching, budgets and purchase requests, with a preview before every change. |
| Full description (≤4000) | the medium description in `listing.md` |
| Supports Dynamic Client Registration | ✓ |
| Categories * (up to 3) | Productivity & Workflow · Analytics & Monitoring · Collaboration Tools |
| Provider / company name | `ProcurementExpress` |
| Website | `https://procurementexpress.com` |
| “Try Now” link | the docs URL |
| Email * | *(the team inbox)* |

**Key features** (≤160 each, at least 3)
1. See the purchase orders waiting for your approval, including delegated approvals.
2. Match supplier invoice lines to PO lines, with ordered, billed and received quantities side by side.
3. Plan single or bulk budget changes from a spreadsheet, with a full before/after review.
4. Forward a supplier email and its PDF becomes a draft purchase request or invoice.
5. Fill in and validate purchase requests, saved as drafts unless you ask to submit.

**Use cases** (≤200 each, at least 2)
1. An approver asks their assistant each morning what is waiting for them and why.
2. Accounts payable clears unmatched invoices by reviewing AI-proposed PO links in one pass.
3. Finance loads next year's budgets from a spreadsheet without retyping a row.

**FAQ** (question ≤200, answer ≤1000, at least 2)
1. **Can the AI approve purchases or pay invoices?** No. It can preview changes and save them after you approve, but approvals and payments stay in ProcurementExpress.
2. **What do I need?** A ProcurementExpress user in an active, paid company, with MCP turned on by a company admin. Nothing to install.
3. **How is access controlled?** OAuth sign-in. You choose the company and each permission; with none ticked, access is read-only. Revoke it any time.

---

## 12. mcp.directory

**How:** https://mcp.directory/submit. Its only required field is "GitHub Repository URL"; there
is no remote URL field, so it lists us from this repo.

| Field | Value |
|---|---|
| GitHub Repository URL | `https://github.com/rubberstamp/procurementexpress-plugins` |
| Short Description | the 100-character tagline in `listing.md` |
| Your Email | *(the team inbox)* |

---

## 13. Cursor Directory

**How:** cursor.directory/plugins/new?type=mcp_server › **Manual** tab (sign in with GitHub or Google).

| Field | Value |
|---|---|
| Name | `ProcurementExpress` |
| Description | the short description in `listing.md` |
| Logo | upload `procurementexpress/assets/logo.png` |
| Repository URL (optional) | `https://github.com/rubberstamp/procurementexpress-plugins` |
| Homepage (optional) | the docs URL |
| Keywords | procurement, purchase orders, invoices, budgets, approvals, finance |
| Component › Type | `MCP Server` |
| Component › Name | `procurementexpress` |
| Component › Content | `{"url": "https://app.procurementexpress.com/mcp"}` |

**One-click install link** (for our docs and the setup page):

```
cursor://anysphere.cursor-deeplink/mcp/install?name=procurementexpress&config=eyJ1cmwiOiJodHRwczovL2FwcC5wcm9jdXJlbWVudGV4cHJlc3MuY29tL21jcCJ9
```

UNVERIFIED: the exact Content format Cursor expects for a remote server. Test the deeplink in
Cursor before publishing it anywhere.

---

## 14. ToolSDK MCP Registry

**How:** pull request to `toolsdk-ai/toolsdk-mcp-registry`. Copy `toolsdk/procurementexpress.json` to
`packages/finance-fintech/procurementexpress.json`, then:

```bash
node scripts/validate-registry.mjs --base origin/main
```
