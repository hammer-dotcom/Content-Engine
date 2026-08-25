---
name: content-gap-analysis
description: Compare what the user has already published against what competitors and the current SERP cover, and surface a list of topics worth writing that the user has no article for yet. Use before keyword-prioritization to build the topic backlog.
---

# Content gap analysis

Find what is missing from the user's content library, not just what is popular. A gap that
a genuine competitor covers and the user does not is worth more than a high-volume term
picked at random from a keyword tool.

## Input

- `your-setup/brand-and-voice.md` for the topics the user's blog covers.
- `your-setup/your-offer.md` for the categories their product competes in.
- Any competitor domains the user has previously mentioned, or ones you find by searching
  the category the user's offer competes in.
- If `content/0-voice-of-customer/backlog.md` exists (from `voice-of-customer-mining` run
  standalone), fold its candidate topics in as well, they carry real buyer language.

## Steps

1. **Map the user's current coverage.** Use Search Console (if on in `data-sources.md`) or
   a `site:` search to see what the user already has published, and what topics and
   subtopics those articles cover.
2. **Map competitor coverage.** For each competitor identified, do the same: what topics do
   they rank for or publish on, that the user does not have equivalent coverage of.
3. **Check the current SERP for the user's category.** For the core terms in the user's
   space, note the subtopics and question types that current top-ranking pages and answer
   engines address, whether or not any specific competitor owns them.
4. **Surface the gaps.** A gap is a topic that is relevant to the user's audience and offer,
   that a competitor or the SERP covers, and that the user has nothing on. Note the specific
   angle available (what the user could say that the existing coverage does not).
5. Do not manufacture gaps that do not fit the user's actual blog or offer. A topic outside
   their category is not a gap, it is noise.

## Output

Write to `content/keyword-ideas.csv` with columns: `keyword, angle, why_it_is_a_gap,
source_competitor_or_serp, funnel_stage_guess`. This is a raw candidate list.
`keyword-prioritization` scores and ranks it next, do not rank here, just surface
candidates honestly.

Never invent a competitor's coverage or a search volume. If you could not verify a gap
exists, note the uncertainty rather than presenting it as fact.
