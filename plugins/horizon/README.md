# horizon (Claude Code plugin)

Adds Horizon's free, no-key MCP server — AI news, the daily AI briefing, and an AI regulation tracker for the EU AI Act, US federal & state bills, and UK policy — plus three skills:

| Skill | Ask it |
|---|---|
| `/ai-news` | "What happened in AI today?" · "Anything from Chinese labs this week?" |
| `/ai-regulation` | "Where does the EU AI Act stand?" · "Any new state AI laws?" |
| `/ai-receipts` | "Is that benchmark claim independently verified?" · "How much of the Anthropic coverage is Anthropic talking?" |

The skills exist because the tools return more than headlines: every item carries the shape of its evidence (self-reported vs independently evaluated, legislative stage from the source). The skills tell Claude to relay that rather than flatten it.

Install:

```
/plugin marketplace add system-alchemist/horizon-mcp
/plugin install horizon@alchemylab
```

Endpoint: `https://horizon.alchemylab.sh/api/mcp` · Docs: https://horizon.alchemylab.sh/developers
