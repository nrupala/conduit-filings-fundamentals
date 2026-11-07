# Conduit — Filings & Fundamentals

A hosted, remote MCP server that gives AI agents live access to SEC EDGAR
data: **24 tools** covering company filings, financial fundamentals,
reportable segments, peer comparisons, and insider transactions.

| | |
|---|---|
| **Endpoint** | `https://mcp.pipavia.com/mcp` |
| **Transport** | Streamable HTTP (stateless JSON-RPC) |
| **Auth** | OAuth 2.1, or API key (`Authorization: Bearer <key>`) |
| **Free tier** | Self-serve key, 100 calls/day |
| **Paid tiers** | Pro and Team, via Paddle — see [pipavia.com](https://pipavia.com) |
| **Registry** | Listed on the Official MCP Registry as `io.github.nrupala/conduit-filings-fundamentals` |
| **Claude** | Approved in Anthropic's Claude Connectors Directory |

## Connect

Point any MCP client at the endpoint:

```json
{
  "mcpServers": {
    "conduit": {
      "url": "https://mcp.pipavia.com/mcp",
      "headers": { "Authorization": "Bearer <your-key>" }
    }
  }
}
```

OAuth 2.1 clients can connect without a key and authorize interactively —
discovery starts at
`https://mcp.pipavia.com/.well-known/oauth-authorization-server`.

## For reviewers

You can test the live server in under a minute, no payment involved:

1. **Mint a free key** — `POST https://mcp.pipavia.com/v1/keys` with a JSON
   body of `{"email": "<your email>"}`. The response contains your key
   (shown once) and its key ID.
2. **Validate it** — `POST https://mcp.pipavia.com/v1/keys/validate` with
   the key in the `Authorization: Bearer <key>` header.
3. **Call the server** — send an MCP `initialize`, then `tools/list`
   (24 tools) and any read-only tool call against
   `https://mcp.pipavia.com/mcp`.

Free keys are metered at 100 calls/day. Every authenticated request,
including `tools/list`, counts against the meter.

## Documentation

- Product site, docs, and checkout: [pipavia.com](https://pipavia.com)
- Terms: [pipavia.com/terms](https://pipavia.com/terms)
- Privacy: [pipavia.com/privacy](https://pipavia.com/privacy)
- Support: [info@pipavia.com](mailto:info@pipavia.com)

## About this repository

This repository is the **public listing** for the hosted service. It
contains documentation and manifests only — no server source code:

- `server.json` — the Official MCP Registry manifest for this server.
- `glama.json` — listing maintenance declaration for Glama.
- `LICENSE` / `NOTICE` — Apache-2.0 terms for the contents of this
  repository.

The hosted service itself is proprietary software operated by
2351485 ALBERTA INC. The Apache-2.0 license in this repository covers the
repository contents only, not the hosted service.

---

Owned by [Nrupal Akolkar](https://nrupalakolkar.com) · Built with
[Muse by Meta](https://muse.ai/join).
