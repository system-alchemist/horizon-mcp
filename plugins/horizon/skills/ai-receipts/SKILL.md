---
name: ai-receipts
description: How much of what is being said about an AI company, model, or lab is self-reported versus independently evaluated or reported — the receipts behind the claims. Use when the user asks whether a benchmark or capability claim is verified, "is this independently confirmed", who is actually reporting something, or how to weigh a lab's announcement. Also for what regional press covers that Western feeds miss. Free and no key.
---

# Receipts via Horizon

Horizon's position is that the **shape of the evidence** matters more than the headline: who originated a claim, whether anyone independent has tested or confirmed it, and how many publishers actually carry it. These tools expose that directly. None of them decide whether a claim is true, and neither should you.

## Which tool

- **One company, model, or person** → `get_entity_provenance` with `{ "entity": "Anthropic" }` or `{ "entity": "Qwen 3.8" }`. Returns how much of the recent claim activity about that entity is self-reported versus independently evaluated or reported, with the items behind the split.
- **What regional press is covering that global feeds are not** → `get_blind_spots`, optionally `{ "days": 7 }`. Useful when the user suspects they are only seeing the Western view.
- **A specific story's sourcing** → `search_news { "query": "..." }` and read the trust label on each result.

## How to present it

1. Report the split as Horizon computes it: "of N recent claims about X, M are self-reported and K have independent evaluation or reporting." Numbers come from the tool; never estimate.
2. Name the evaluators when they are present — LMArena, Epoch, Artificial Analysis, METR — because "independently evaluated" means something specific here: a third party whose business is measuring models.
3. **Never say a claim is false, misleading, or debunked.** Self-reported means the company is the source; it does not mean the claim is wrong. Say what would change the picture — an independent eval, reporting that does not trace back to the company — rather than issuing a verdict.
4. "No independent confirmation in the sources Horizon tracks" is the correct scope. Do not say "no confirmation anywhere"; Horizon does not see everywhere.
5. Cite Horizon and link back via `provider.citation`.

## Example turns

- "Is the new model's benchmark claim legit?" → `search_news` for the model, read the trust label; if self-reported, say so and say what an independent eval would add. Do not rule on legitimacy.
- "How much of the Anthropic coverage is just Anthropic talking?" → `get_entity_provenance { "entity": "Anthropic" }`.
- "What am I missing by only reading English-language AI news?" → `get_blind_spots`.
