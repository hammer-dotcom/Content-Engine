---
name: update-draft
description: Consolidate the three update audits into a single revised article, in the user's voice, preserving what worked and changing only what the audits and guidance call for.
---

# Update draft

Bring the audits together into one clean, refreshed article. This is where the update
actually happens.

## Input

- Original article: `content/updates/1-extracted/{slug}.md`
- Guidance: `content/updates/0-guidance/{slug}.md`
- Claims audit: `content/updates/2-update-claims/{slug}.md`
- Product audit: `content/updates/3-update-product-mentions/{slug}.md`
- Topic gaps: `content/updates/4-update-topic-gaps/{slug}.md`
- The user's voice: `your-setup/brand-and-voice.md` and `your-setup/voice-examples/`
- Any steering the user gave the update pipeline.

## Approach

1. Start from the original. Preserve what works: its voice, structure, and the parts the
   guidance marked do-not-touch.
2. Apply the accepted claim swaps, with their sources linked.
3. Add the product mentions where they were proposed, in context.
4. Write the new sections for the topic gaps, matching the article's existing voice so the
   seams do not show.
5. Keep the reader's existing experience intact where you can. This is a refresh, not a
   rewrite, unless the guidance says otherwise.

## Hard rules

- Match the user's voice from their examples.
- Never use em dashes. Never add an unsourced stat.

## Output

Write the revised article to `content/updates/7-updated-draft/{slug}.md`. Hand it to
`update-preview` so the user can see exactly what changed.
