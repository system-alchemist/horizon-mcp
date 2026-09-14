# Horizon — AI news & AI regulation tracker for agents (MCP)

A free, no-key MCP server for **AI news** and **AI regulation tracking** — the EU AI Act, US federal and state bills, UK policy — plus a daily AI briefing, all with the evidence behind each claim labelled: self-reported by the company, or independently reported and evaluated.

- **Endpoint:** `https://horizon.alchemylab.sh/api/mcp` (streamable HTTP, no auth)
- **Live tracker:** https://horizon.alchemylab.sh/ai-regulation-tracker
- **Daily briefing archive:** https://horizon.alchemylab.sh/briefing
- **Setup for Claude, Cursor, ChatGPT and others:** https://horizon.alchemylab.sh/developers
- **Official MCP registry name:** `sh.alchemylab.horizon/briefing`

## Claude Code plugin

Adds the MCP server and three skills — `/ai-news`, `/ai-regulation`, `/ai-receipts` — that teach Claude which tool answers which question and how to relay the evidence labels instead of flattening them into headlines.

```
/plugin marketplace add system-alchemist/horizon-mcp
/plugin install horizon@alchemylab
```

Then ask: *"What's the state of the EU AI Act?"* — or `/ai-regulation`, `/ai-news`, `/ai-receipts` directly.

## Any other MCP host

Point it at the endpoint. No key, no OAuth:

```json
{ "mcpServers": { "horizon": { "url": "https://horizon.alchemylab.sh/api/mcp" } } }
```

For hosts that only speak stdio, `npx mcp-remote https://horizon.alchemylab.sh/api/mcp` bridges it.

## Tools

| Tool | What it answers |
|---|---|
| `get_daily_briefing` | What happened in AI today, or on any past date (public archive) |
| `get_regulation_updates` | Current AI legislation with its stage — `eu`, `us_federal`, `us_state`, `uk` |
| `get_entity_provenance` | How much of the talk about a company or model is self-reported vs independently evaluated |
| `get_topic_signal` | Recent signal on models, regulation, research, funding, tools… |
| `get_region_signal` / `get_china_signal` | What Chinese, Korean, Japanese or EU press is covering |
| `get_blind_spots` | What regional press covers that Western feeds miss |
| `search_news` | Quick relevance check, top 3 |
| `get_new_since` / `get_related` | Incremental polling and "more like this" |
| `list_sources` | What the corpus covers |

Key-gated: `ask_horizon` (cited answers) and `get_trends` — see [/developers](https://horizon.alchemylab.sh/developers).

## What makes it different

Most AI-news tools give you headlines. Horizon labels **who is saying it**: a lab's own benchmark number carries "self-reported, no independent confirmation"; a number measured by LMArena, Epoch, Artificial Analysis or METR carries "independently evaluated". Regulation items carry their legislative stage from the source, not from coverage. Nothing is ever marked true or false — the shape of the evidence is the product.

Sources: Hacker News, Reddit, Lobsters, Bluesky, curated lab and media RSS, arXiv, Hugging Face, ModelScope, US Congress and federal agencies, US state legislatures, UK Parliament, EU bodies. Regional lenses for China, Korea, Japan and the EU.

## License

MIT. Attribution requested: name "Horizon" and link https://horizon.alchemylab.sh when you use results; every result carries a ready-to-paste `provider.citation`.
