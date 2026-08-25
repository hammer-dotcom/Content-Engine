---
name: research
description: Gather everything needed before writing about a keyword: search intent, what currently ranks, the questions readers ask, and the gaps worth filling. Produces a research brief.
---

# Research

Build the research brief that every later step relies on. Good content starts here, not at
drafting. Do not skip to writing.

## Input

A keyword or topic, plus any steering context the user gave the pipeline.

## How to run

Check `your-setup/data-sources.md`. Use Google Search Console MCP and/or DataForSEO MCP for
keyword and SERP data if they are on; otherwise use built-in web search and mark metrics as
estimates.

## Steps

1. **Search intent.** What does someone searching this actually want? Informational,
   comparison, how-to? Name the dominant intent.
2. **What ranks now.** Look at the current top results. For each, note the angle, the
   headers, and the format (listicle, guide, opinion). Summarise the consensus view.
3. **Questions readers ask.** Collect the real questions around this topic and group them
   into themes, so the article answers them without turning into FAQ spam.
4. **Voice of customer.** If `voice-of-customer-mining` has produced a file for this topic
   (in `content/0-voice-of-customer/`), pull in the real buyer language, pain points, and
   objections it found. This is the B2B edge keyword tools miss: phrasing and concerns that
   come straight from sales calls, interviews, and tickets. If no VoC file exists, note that
   the brief would be stronger with one.
5. **Answer-engine view.** Check what AI answer engines (ChatGPT, Perplexity, Google AI
   Overviews) currently say about this topic and, importantly, **which sources they cite**.
   This shows the consensus you need to match and the angle that could earn a citation. If
   `answer-engine-audit` has produced a file for this topic, use it.
6. **Competitor teardown nuggets.** For comparison or "vs" topics, gather specific, real
   points from review sites, changelogs, and public sources (pricing changes, common
   complaints, missing features). Note the source for each: every claim must be citable.
7. **Gaps and angles.** Where do the ranking articles and answer engines agree, and where is
   there room to say something more useful, more current, or more specific? This is where the
   article earns its place, and where original data or the user's POV belongs.
8. **Related terms and subtopics** worth covering, with parent topic if available.

## Output

Write a clear brief to `content/1-research/{slug}.md` with sections for intent, what ranks,
question themes, voice of customer, answer-engine view, competitor nuggets, gaps and angles,
and related subtopics. Keep it skimmable. This is handed to `your-reference` and `outline`.

Never invent volumes, traffic numbers, or competitor claims. Every claim about a competitor
or the market needs a real, retrievable source. If you could not measure something, say so.
