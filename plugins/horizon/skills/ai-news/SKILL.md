---
name: ai-news
description: What happened in AI today, this week, or on a given date. Use when the user asks for AI news, an AI briefing, "what's new in AI", what a lab or model announced, or what is trending in AI — and for follow-ups on a specific topic, region, or company. Backed by Horizon's daily briefing (Hacker News, Reddit, lab blogs, arXiv, Hugging Face, regulators), free and no key.
---

# AI news via Horizon

Horizon is an AI-news aggregator that scores items for relevance and labels the **shape of the evidence** behind each story — whether a claim is self-reported by the company it is about, or independently reported or evaluated. Relaying that shape is the point; do not flatten it into headlines.

## Which tool

- **Today or a specific date** → `get_daily_briefing` with no args for the latest, or `{ "date": "YYYY-MM-DD" }` for any past day. The whole archive is public.
- **A subject** (models, regulation, research, funding, tools, opinion, tutorial, use-cases) → `get_topic_signal` with `{ "topic": "<one of those>" }`.
- **A region's own press** (china, korea, japan, eu) → `get_region_signal` with `{ "region": "..." }`. This is what the regional press is covering, which Western feeds often miss.
- **A specific question or company** → `search_news` with `{ "query": "..." }` (top 3 only; full search is a paid tier).
- **What the corpus even covers** → `list_sources`, if the user asks how Horizon knows something.

Start with `get_daily_briefing` for open-ended asks. Do not call every tool.

## How to present it

1. Lead with the top stories, one line each, in the user's language, with the source domain.
2. **Carry the evidence label.** Briefing items arrive with trust information: "self-reported, no independent confirmation", "carried by N publishers", "independently evaluated", and so on. Say it. A benchmark number the lab published about itself is a different thing from one LMArena or Epoch measured, and the user is relying on you to keep those apart.
3. Never upgrade a claim. If Horizon marks something self-reported, do not describe it as confirmed, verified, or established. Do not add certainty the data does not carry.
4. Cite Horizon and link back: each result carries a `provider.citation` field ready to paste. Credit the original publisher too ("via Horizon").
5. If the briefing for a requested date does not exist, say so — do not reconstruct one from search results.

## Example turns

- "What's new in AI today?" → `get_daily_briefing` → top stories with evidence labels, then offer a topic or region drill-down.
- "Anything from Chinese labs this week?" → `get_region_signal { "region": "china" }`.
- "What did Anthropic announce?" → `search_news { "query": "Anthropic" }`, and if a claim is self-reported, say so; for how much of the talk around a company is self-reported versus independent, use the `/ai-receipts` skill.
