---
description: Run the full content creation pipeline on a keyword, from research to a styled preview. Usage: /blog-pipeline "keyword" [optional steering notes]
argument-hint: "keyword" [notes to steer the article]
---

Run the full blog creation pipeline for: **$ARGUMENTS**

## First, check the setup gate

Before anything else, follow RULE 1 in `CLAUDE.md`. Scan `your-setup/` for any
`{{REPLACE_ME}}` token or `<!-- SETUP_INCOMPLETE -->` line. If found, STOP and tell the
user to run `/setup`. Do not continue.

**If setup is complete (no markers found), the gate has done its job. Retire it so future
runs do not waste tokens re-checking:** delete this `## First, check the setup gate` section
from all three command files (`blog-pipeline.md`, `update-pipeline.md`, `llms-brand-page.md`)
and delete RULE 1 from `CLAUDE.md`. Do this once, then continue with the run.

## Parse the input

- The first quoted phrase is the **keyword** or topic.
- Anything after it is **steering context**: angles to take, sub-topics to cover,
  products to feature, things to avoid. This is the user's front-loaded direction and it
  shapes every step. Save it to `content/1-research/{slug}-context.md`.
- Derive a **slug** from the keyword (lowercase, words joined by hyphens). Use the same
  slug for every output file so the article's files stay together.

## Run these skills in order, saving each output

For each step, **invoke the named skill with the Skill tool**. Do not perform the step from
memory: the skill file holds the current instructions and must be loaded each run. When the
skill returns, save its output file, then move to the next step. The saved files are how the
user debugs a bad result, so never skip them. If you skip a conditional step, say so.

1. **voice-of-customer-mining** *(conditional)*. Invoke only if `inputs/voice-of-customer/`
   contains files. It mines real buyer language and pain points -> `content/0-voice-of-customer/{slug}.md`.
   If the folder is empty, the skill will surface a one-time nudge to add material; report
   that and continue.
2. **content-gap-analysis** -> `content/keyword-ideas.csv`
3. **keyword-prioritization** -> updates `content/keyword-ideas.csv` with scores
4. **research** -> `content/1-research/{slug}.md`
5. **answer-engine-audit** (topic mode) -> `content/1-research/{slug}-aeo.md`
6. **your-reference** -> `content/2-reference/{slug}.md`
7. **outline** -> `content/3-outlines/{slug}.md`
8. **product-mentions** -> `content/4-outlines-annotated/{slug}.md`
9. **draft** -> `content/5-drafts/{slug}.md`
10. **verify-claims** -> `content/6-drafts-cited/{slug}.md`
11. **visuals** (only if turned on in `your-setup/data-sources.md`) -> `content/images/{slug}/`
12. **preview** -> `content/7-preview/{slug}.html`

Steps 2 and 3 only need to run once to build a topic backlog, not on every single article.
If the user gave you a keyword directly (rather than asking "what should I write about"),
skip straight to step 4 and note that you skipped the backlog-building steps because they
already had a topic.

Apply the steering context and the user's `your-setup/` files at every relevant step.

## When done

Tell the user where each file is, open or point them to the HTML preview, and ask if they
want to adjust any single step (you can re-run just that skill) or format it for publishing
with the `format-for-publish` skill.

Do not invent data. Follow the data-source toggles. Never use em dashes.
