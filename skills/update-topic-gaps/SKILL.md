---
name: update-topic-gaps
description: Compare an existing article against what currently ranks for its topic and find sections or subtopics it now misses, so the refresh covers what readers expect today.
---

# Update topic gaps

What readers expect from a topic moves over time. This finds where an older article has
fallen behind the current SERP.

## Input

- Extracted article: `content/updates/1-extracted/{slug}.md`
- Priorities: `content/updates/0-guidance/{slug}.md`

## Steps

1. Identify the article's target topic or keyword.
2. Look at what currently ranks for it. Use Google Search Console MCP or DataForSEO MCP if
   on, otherwise built-in web search of the current top results.
3. **Also check what answer engines cover and cite.** Ask ChatGPT, Perplexity, or AI
   Overviews the core question behind this topic and note the subtopics they include and the
   sources they cite. A gap that answer engines treat as essential matters even if the SERP
   does not show it yet. If `answer-engine-audit` produced a file for this topic, use it.
4. Extract the subtopics, sections, questions, and **decision factors** (integrations,
   pricing, support, compliance, comparisons) that those results and answers cover.
5. Compare against the article. Find genuine gaps: things the reader, or an answer engine
   summarising the category, would now expect that the article does not address.
6. For each gap, propose a section or addition, and where it should slot in. Skip gaps that
   do not fit the article's angle or the user's guidance.

## Output

Write to `content/updates/4-update-topic-gaps/{slug}.md`: the proposed new sections with
placement and a one-line reason each. Feeds into `update-draft`.
