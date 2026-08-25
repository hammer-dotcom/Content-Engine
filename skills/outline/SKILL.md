---
name: outline
description: Turn the research and reference into a structured H2/H3 outline where every section leads with its most important point and the whole thing covers the topic without overlap.
---

# Outline

Build the skeleton of the article. A strong outline makes the draft almost write itself.

## Input

- Research brief: `content/1-research/{slug}.md`
- Reference notes: `content/2-reference/{slug}.md`
- Any steering context the user provided.

## Principles

- **Lead with the point.** Every section opens with its most important idea, then adds the
  example, context, or nuance after. Do not warm up to the point.
- **Mutually exclusive, collectively exhaustive.** Cover the topic fully, but do not let
  sections overlap. Each H2 earns its place.
- **Headers support the title.** Every header should make sense under the article's promise.
- **Build for answer engines.** Phrase each section so it can be lifted and cited. Use clear,
  question-shaped or claim-shaped headers, and make sure the opening sentence of each section
  is a self-contained, quotable answer. This is how the piece earns citations in ChatGPT,
  Perplexity, and AI Overviews, not just rankings.
- **Map to the buyer journey.** For B2B, tag each section with the stage it serves (problem-
  aware, solution-aware, comparison, decision). A bottom-of-funnel piece should spend most of
  its weight near the decision end.
- **Add a comparison section for mid-funnel topics.** For "vs", "best", or "alternatives"
  topics, plan a comparison table covering the decision factors buyers actually weigh
  (integrations, pricing model, support, compliance, fit). These pages are critical mid-funnel.
- Match the structure the user's voice examples favour (from `your-setup/`).

## Output

Write to `content/3-outlines/{slug}.md`:

- A working **title** and a one-line angle.
- A **hook** idea for the intro.
- Each **H2** (and H3s where needed) with, under it: the key point that section makes, any
  specific example, data, or table to include, and which internal link from the reference
  notes belongs there.

Keep it tight. This is the bones, not the prose. Hand it to `product-mentions` next.
