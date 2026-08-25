---
name: update-guidance
description: Set the priorities for an article refresh before running the audits, folding in the user's own steering on what to focus on and what to leave alone.
---

# Update guidance

Decide what this refresh is for before changing anything. A quick planning step that keeps
the update focused instead of rewriting things that were fine.

## Input

- Extracted article: `content/updates/1-extracted/{slug}.md`
- Any steering context the user gave the update pipeline.

## Steps

1. Skim the article and form a view of its current state: what still holds up, what looks
   dated, what is thin.
2. **Triage the content type.** Decide whether this piece is worth refreshing at all. Generic
   top-of-funnel explainers are the content type AI Overviews and answer engines have hit
   hardest, so a refresh may not pay back. A specific, decision-stage, or product-tied piece
   is usually worth the effort. Say which this is and whether to proceed, slim down, or
   consolidate it into a stronger page.
3. **Judge success beyond traffic.** Many good B2B pages now show "traffic down, revenue up":
   they still influence buyers and get cited by answer engines even as sessions fall. Do not
   treat a traffic dip as proof the page failed. Note whether the goal of this refresh is
   traffic, citations and brand representation, or conversion, because that changes the edits.
4. Fold in the user's steering. If they said focus on X or leave Y alone, that wins.
5. Set clear priorities across the audits that follow: outdated claims, missing product or
   feature mentions, and topic gaps versus the current SERP and answer engines.
6. Note anything off-limits: sections the user does not want touched, a voice or angle to
   preserve.

## Output

Write to `content/updates/0-guidance/{slug}.md`: the goal of this refresh, the priorities
in order, and any do-not-touch notes. The audit skills read this so they pull in one
direction.
