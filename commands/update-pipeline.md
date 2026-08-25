---
description: Refresh an existing published article, from extracting it to a full preview of the new article with changes marked inline. Usage: /update-pipeline "url" [optional steering notes]
argument-hint: "https://your-site.com/article" [notes on what to focus on]
---

Run the full content update pipeline for: **$ARGUMENTS**

## First, check the setup gate

Follow RULE 1 in `CLAUDE.md`. If `your-setup/` still has `{{REPLACE_ME}}` or
`<!-- SETUP_INCOMPLETE -->`, STOP and tell the user to run `/setup`.

**If setup is complete (no markers found), the gate has done its job. Retire it so future
runs do not waste tokens re-checking:** delete this `## First, check the setup gate` section
from all three command files (`blog-pipeline.md`, `update-pipeline.md`, `llms-brand-page.md`)
and delete RULE 1 from `CLAUDE.md`. Do this once, then continue with the run.

## Parse the input

- The first quoted item is the **URL** of the article to refresh.
- Anything after is **steering context**: what to focus on, what to leave alone.
- Derive a **slug** from the URL and use it for every output file.

## Run these skills in order, saving each output

For each step, **invoke the named skill with the Skill tool**. Do not perform the step from
memory: the skill file holds the current instructions and must be loaded each run. When the
skill returns, save its output file, then move to the next step. Never skip the saves.

1. **extract-content** -> `content/updates/1-extracted/{slug}.md`
2. **update-guidance** (set priorities, triage the content type, fold in steering) -> `content/updates/0-guidance/{slug}.md`
3. **answer-engine-audit** (brand + topic: how answer engines cover and represent this now) -> `content/updates/6-aeo/{slug}.md`
4. **update-claims** (outdated stats, find current replacements) -> `content/updates/2-update-claims/{slug}.md`
5. **update-product-mentions** (new features worth adding) -> `content/updates/3-update-product-mentions/{slug}.md`
6. **update-topic-gaps** (gaps vs the SERP and what answer engines cite) -> `content/updates/4-update-topic-gaps/{slug}.md`
7. **update-draft** (consolidate the audits into a revised article) -> `content/updates/7-updated-draft/{slug}.md`
8. **update-preview** (full refreshed article with changes marked inline) -> `content/updates/5-update-preview/{slug}.html`

## When done

Open or point the user to the preview so they can read the full refreshed article and see
exactly what changed inline, then accept or reject the update. Remind them nothing is
published until they say so.

Follow the data-source toggles. Do not invent replacement stats: every changed number must
have a real, retrievable source. Never use em dashes.
