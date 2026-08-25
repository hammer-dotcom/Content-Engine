---
name: update-claims
description: Audit an existing article for outdated stats and facts, find current verified replacements, and propose the swaps for the user to accept.
---

# Update claims

Find what has gone stale and fix it with current, sourced facts. The most valuable part of
refreshing old content.

## Input

- Extracted article: `content/updates/1-extracted/{slug}.md`
- Priorities: `content/updates/0-guidance/{slug}.md`

## Steps

1. List every factual claim, statistic, date, and named fact in the article.
2. For each, check whether it is still current. Use the data tools that are on, plus
   built-in web search.
3. Where something is outdated, find the current figure from a real, retrievable source.
4. Propose the swap: old value, new value, the source, and a confidence note.
5. Flag claims you cannot verify either way so the user can decide.

## Hard rule

Never invent a replacement number. Every proposed swap must have a real source. If you
cannot find one, say the claim needs the user's judgement rather than guessing. Claims about
competitors or the market get the strictest treatment: link a real source (review site,
changelog, primary doc) or cut the claim. Unsourced competitor claims are hearsay and a risk.

## Output

Write to `content/updates/2-update-claims/{slug}.md`: a table of proposed changes (old,
new, source, confidence) plus flagged claims. These feed into `update-draft`.
