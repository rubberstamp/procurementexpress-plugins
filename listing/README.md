# Listing the ProcurementExpress MCP in MCP directories

Run every command below from this `listing/` folder.

| File | Use |
|---|---|
| `listing.md` | Master copy: names, taglines, descriptions, tags, tools, prompts, FAQ, config snippets |
| `store-fields.md` | Per-store form fields with ready values |
| `server.json` | Official MCP Registry entry (validates against the 2025-12-11 schema) |
| `docker/procurementexpress/` | Docker MCP Catalog PR files (`server.yaml`, `tools.json`, `readme.md`) |
| `toolsdk/procurementexpress.json` | ToolSDK registry PR file |
| `lobehub/lhm.plugin.json` | LobeHub `lhm` CLI manifest |

## Order

1. **Official MCP Registry.** MCPfinder, PulseMCP and Glama read from it, so it covers several stores.
2. **Free forms:** MCP.so (remote tab), mcpservers.org, Cursor Directory.
3. **Pull requests:** Docker MCP Catalog (test OAuth first), ToolSDK.
4. **Paid, optional:** MCP Market ($69, the only option for remote servers), the paid fast lanes of MCP.so / mcpservers.org ($39).
5. **From this repo:** LobeHub (`lhm` CLI), mcp.directory (form).
6. **Cannot submit now:** Smithery (closed 31 Oct 2026), PulseMCP (paused), AIbase (no route found).

## Publishing to the Official MCP Registry

The name `com.procurementexpress/mcp` needs proof that we own `procurementexpress.com`.
Use **DNS**: an HTTP proof would have to sit on the bare `procurementexpress.com` (the marketing
site), and a file on `app.procurementexpress.com` only covers `com.procurementexpress.app/*`.

```bash
# 1. Install the CLI
brew install mcp-publisher

# 2. Make a key (OpenSSL 3+; macOS's LibreSSL fails). Keep key.pem in the team password vault, never in git.
openssl genpkey -algorithm Ed25519 -out key.pem
echo "v=MCPv1; k=ed25519; p=$(openssl pkey -in key.pem -pubout -outform DER | tail -c 32 | base64)"
```

3. Add that line as a **TXT record on the apex** `procurementexpress.com` (not a subdomain). Wait for it to resolve:

```bash
dig +short TXT procurementexpress.com | grep MCPv1
```

4. Log in and publish from this folder:

```bash
PRIVATE_KEY="$(openssl pkey -in key.pem -noout -text | grep -A3 'priv:' | tail -n +2 | tr -d ' :\n')"
mcp-publisher login dns --domain procurementexpress.com --private-key "$PRIVATE_KEY"
mcp-publisher publish
curl -s "https://registry.modelcontextprotocol.io/v0.1/servers?search=com.procurementexpress/mcp"
```

To update the listing later, bump `version` in `server.json` and publish again.

## Before you submit anywhere

- [ ] Confirm the support address in `listing.md` (`support@procurementexpress.com`).
- [ ] Decide on a team inbox for the "Email" fields.
- [ ] Some stores want a 512×512 icon. The largest we have is 310×310 (`procurementexpress/assets/logo.png`).

## Tracker

| # | Store | Method | Status | Listing URL |
|---|---|---|---|---|
| 1 | Official MCP Registry | CLI | not started | |
| 2 | Glama | auto from registry / claim | not started | |
| 3 | Smithery | closed | blocked | |
| 4 | MCP.so | form | not started | |
| 5 | PulseMCP | auto from registry (paused) | blocked | |
| 6 | MCPfinder | auto from registry | not started | |
| 7 | mcpservers.org | form | not started | |
| 8 | AIbase MCP | no route | blocked | |
| 9 | Docker MCP Catalog | PR | not started | |
| 10 | LobeHub | CLI from this repo | not started | |
| 11 | MCP Market | form ($69) | not started | |
| 12 | mcp.directory | form (this repo) | not started | |
| 13 | Cursor Directory | form | not started | |
| 14 | ToolSDK | PR | not started | |
