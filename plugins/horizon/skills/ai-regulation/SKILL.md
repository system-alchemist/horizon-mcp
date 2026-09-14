---
name: ai-regulation
description: The current state of AI regulation and AI legislation — the EU AI Act, US federal bills and agency actions, US state AI laws, and UK AI policy — with each item's legislative stage. Use when the user asks where a law stands, what AI regulation passed or is proposed, "AI Act status", "AI regulation tracker", or what an AI bill does. Live, sourced from Congress, state legislatures, UK Parliament and EU bodies; free and no key.
---

# AI regulation via Horizon

Horizon tracks AI legislation across four jurisdictions and records each item's **stage** — proposed, in committee, passed, enacted, in force — from the legislative source itself, not from news coverage of it.

## Which tool

`get_regulation_updates`, optionally narrowed:

- `{ "jurisdiction": "eu" }` — European Union (the EU AI Act and its implementing acts)
- `{ "jurisdiction": "us_federal" }` — US Congress and federal agencies
- `{ "jurisdiction": "us_state" }` — US state legislatures (California, Colorado, New York, Texas and others)
- `{ "jurisdiction": "uk" }` — UK Parliament and government
- No args — everything, most recent first

Add `"limit"` to control volume. One call is usually enough; call per jurisdiction only when the user is comparing them.

## How to present it

1. Group by jurisdiction. For each item: title, **stage**, date, and the source link. The stage is the fact the user came for — a bill "in committee" and a law "in force" must never be described the same way.
2. Do not predict outcomes or characterise a bill as likely to pass. Report the stage Horizon recorded and the date it was recorded.
3. If a jurisdiction the user asked about returns nothing, say Horizon has no recent items for it. Do not fill the gap from memory — your training data is older than this feed, and regulation is exactly where stale knowledge misleads.
4. When the user asks "what does the EU AI Act say about X", the tracker gives status and links, not legal analysis. Point to the linked source text for the substance and be clear about the difference.
5. Cite Horizon and link back using the `provider.citation` field on each result. The public tracker page is https://horizon.alchemylab.sh/ai-regulation-tracker.

## Example turns

- "Where does the EU AI Act stand?" → `get_regulation_updates { "jurisdiction": "eu" }` → items with stages, most recent first, source-linked.
- "Any new state AI laws?" → `get_regulation_updates { "jurisdiction": "us_state" }`.
- "Compare US and UK approaches" → two calls, then present side by side by stage — not by your own summary of each country's philosophy.
