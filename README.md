# Horizon AI Intelligence — MCP Server

> Free AI-industry intelligence for agents: daily briefings, a US/UK/EU regulation tracker, and China/EU/South-America regional lenses.

**Horizon** is a hosted, remote [Model Context Protocol](https://modelcontextprotocol.io) server that gives any MCP-capable agent a single, cheap call for *"what's happening in AI right now."* It aggregates Hacker News, Reddit, arXiv, Hugging Face, ModelScope, lab blogs and more, LLM-scores everything for relevance, and exposes daily briefings, a live regulation tracker, regional lenses, and semantic search.

- **Endpoint:** `https://horizon.alchemylab.sh/api/mcp` (streamable-HTTP)
- **Auth:** none for the read tools
- **Docs & full API:** https://horizon.alchemylab.sh/developers
- **In the official MCP registry as:** `sh.alchemylab.horizon/briefing`

> This repository is **documentation only** — Horizon is a hosted service that's always on. There's nothing to install, build, or run locally.

## Quick start

Point any MCP client at the remote endpoint via the [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) shim:

```json
{
  "mcpServers": {
    "horizon": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://horizon.alchemylab.sh/api/mcp"]
    }
  }
}
```

Drop that into your client config (`claude_desktop_config.json`, Cursor, Cline, etc.) and the Horizon tools appear. No API key is needed for the read tools.

## Tools

The read tools are free and need no auth. See **https://horizon.alchemylab.sh/developers** for the always-current list and full schemas.

| Tool | What it does |
|---|---|
| `get_daily_briefing` | Today's AI briefing — top stories, emerging signals, new entrants |
| `get_regulation_updates` | Live US / UK / EU AI-regulation tracker with stage timelines |
| `get_topic_signal` | Momentum on a topic over a time window |
| `get_region_signal` | Regional lens — `china`, `eu`, or `south-america` |
| `search_news` | Full-text search across the recent corpus (teaser results) |
| `get_new_since` | Incremental delta poll (cursor-based) for polling agents |
| `get_related` | Semantic "more like this" for a given item |
| `list_sources` | The ingested source catalogue |
| `ask_horizon` | Synthesized, cited answer over the recent corpus *(needs an API key)* |
| `get_trends` | The week's rising models, labs & people by momentum *(Pro — needs an API key)* |

Every item tool also returns `structuredContent` for easy parsing.

## REST (no MCP client needed)

The cheapest single fetch for "what happened in AI today":

```bash
curl https://horizon.alchemylab.sh/briefing.md            # today's briefing, markdown
curl https://horizon.alchemylab.sh/api/public/briefing    # same, JSON (add ?format=md)
curl https://horizon.alchemylab.sh/api/public/regulations # US/UK/EU AI legislation + stages
```

Machine-readable index: https://horizon.alchemylab.sh/llms.txt

## Full API (key-gated)

Subscribers mint API keys at https://horizon.alchemylab.sh/api-keys for the `/api/v1` tier — full-text search, full bodies, complete history, webhooks, and the cited `ask_horizon` answer endpoint. Import the OpenAPI 3.1 spec at https://horizon.alchemylab.sh/openapi.json into GPT Actions, LangChain, or any tool-caller to auto-generate a typed client.

## Links

- **Website:** https://horizon.alchemylab.sh
- **Developer quickstart:** https://horizon.alchemylab.sh/developers
- **Also on Smithery:** https://smithery.ai/servers/alix-petkov/horizon
- **Official MCP registry:** `sh.alchemylab.horizon/briefing`

## License

[MIT](LICENSE) — covers this documentation repository. The Horizon service itself is a hosted product.
