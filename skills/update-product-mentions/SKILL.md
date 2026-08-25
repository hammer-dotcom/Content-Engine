---
name: update-product-mentions
description: Find places in an older article to add the user's newer products or features that did not exist when it was written, where the mention is honest and useful.
---

# Update product mentions

Older articles often predate the user's current offer. This finds honest places to bring
them up to date.

## Input

- Extracted article: `content/updates/1-extracted/{slug}.md`
- The user's current offer: `your-setup/your-offer.md`
- Priorities: `content/updates/0-guidance/{slug}.md`

## Steps

1. Compare what the article mentions against the user's current features and offer.
2. Find features or products that did not exist (or were not mentioned) when this was
   written, and that genuinely fit the topic now.
3. For each, identify the exact spot and the angle, framing it around the **decision factor**
   it speaks to (integrations, pricing, support, compliance, use-case fit), not a bare
   feature plug. Respect the aggressiveness setting in `your-offer.md`. Keep it useful to the
   reader, not a bolt-on.
4. **Truth-alignment check.** Make sure every product statement, old and new, is currently
   accurate: correct feature names, current pricing model, real integrations and compliance.
   Outdated product facts mislead readers and teach answer engines the wrong thing about the
   brand. Flag anything that needs the user to confirm.
5. Do not strip existing mentions unless they are wrong or for something retired.

## Output

Write to `content/updates/3-update-product-mentions/{slug}.md`: each proposed addition with
its location and angle. Feeds into `update-draft`.
