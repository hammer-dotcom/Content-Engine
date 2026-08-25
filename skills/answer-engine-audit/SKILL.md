---
name: answer-engine-audit
description: Check what AI answer engines (ChatGPT, Perplexity, Google AI Overviews, Claude) currently say about a topic or the user's brand, and which sources they cite. Use early in content creation and updates, and inside the llms-brand-page command.
---

# Answer-engine audit

Search is no longer ten blue links. Buyers ask ChatGPT, Perplexity, and Google's AI mode and
read a synthesised answer. Ranking is not enough; you need to be the source the answer cites,
and you need the answer about your brand to be accurate. This skill checks both.

## Two modes

### Topic mode (used in the pipelines)

For a given keyword or topic:

1. Pose the core question behind the topic to the answer engines you can reach (built-in web
   search of AI Overviews and live queries to any AI tools available). Capture the consensus
   answer they give.
2. Note **which sources they cite** and which sites keep reappearing. These are the pages
   winning the citation, and the bar to clear.
3. Identify the **angle or evidence** that is missing from the current answer, where original
   data, a clearer definition, or the user's POV could earn the citation instead.
4. Note the **decision factors** the answers emphasise for the category.

### Brand mode (used by `/llms-brand-page` and updates)

For the user's brand:

1. Ask the answer engines who the user is, what they do, who they are for, and how they
   compare to named competitors.
2. Record what is **accurate**, what is **outdated**, and what is **missing or wrong**. This
   is the truth-alignment gap: the difference between reality and what the models believe.
3. Note where the brand is absent from answers it should appear in (for example "best X for
   Y" prompts), and which competitors show up instead.

## Honesty

Report only what the engines actually return. Do not guess what an answer engine "probably"
says. If you cannot reach a given engine, say which ones you checked and how. Quote answers
accurately, do not embellish.

## Output

- Topic mode: write to `content/1-research/{slug}-aeo.md` (consensus answer, who gets cited,
  the citation gap, decision factors). Feeds `research`, `outline`, and `update-topic-gaps`.
- Brand mode: write to `content/answer-engine-audit/brand.md` (accurate, outdated, missing,
  competitor presence). Feeds `/llms-brand-page` and update guidance.
