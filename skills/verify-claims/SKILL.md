---
name: verify-claims
description: Go through a draft, find every factual claim and statistic, find a real source for each, add the hyperlink, and flag anything that cannot be verified.
---

# Verify claims

Make the article trustworthy. This step is why the engine can be trusted at scale: it
checks the facts rather than hoping they are right.

## Input

Draft: `content/5-drafts/{slug}.md`.

## Steps

1. Read the draft and list every factual claim, statistic, and named fact.
2. For each, find a real, current, retrievable source. Prefer primary sources over
   summaries. Use the data tools that are on in `your-setup/data-sources.md`, plus
   built-in web search.
   - **Competitor and market claims get the strictest treatment.** Any statement about a
     rival ("their pricing went up", "users complain about X") must link to a real source:
     a review site, a changelog, a primary doc. An unsourced competitor claim is hearsay and
     a legal risk. Cite it or cut it.
3. Add the source as a hyperlink at the claim, or as a citation, matching how the user's
   voice examples handle sourcing.
4. **Flag anything you cannot verify.** Do not quietly leave an unsourced stat in. Mark it
   clearly so the user can fix or cut it. If a number turns out to be wrong or outdated,
   correct it and note the change.
5. Confirm internal links from earlier steps still point somewhere sensible.

## Hard rule

Never fabricate a source, URL, statistic, or quote. If you cannot find a real source for a
claim, say so and flag the claim. An honest gap is better than an invented citation.

## Output

Write the cited draft to `content/6-drafts-cited/{slug}.md`, with a short list at the end
of any claims you flagged for the user's attention.
