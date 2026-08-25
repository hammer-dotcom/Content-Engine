---
description: Build an LLM-readable brand page so answer engines describe you accurately. A site-level asset, generated once and refreshed periodically. Usage: /llms-brand-page
argument-hint: (optional notes on positioning or what to emphasise)
---

Build the user's LLM-readable brand page. Optional steering: **$ARGUMENTS**

This is a site-level asset, not a per-article output. Answer engines form a view of the
user's brand from across the web; this page gives them one clear, accurate source to draw
from, covering key points, decision factors, and company facts. Run it once, then refresh
when the offer changes.

## First, check the setup gate

Follow RULE 1 in `CLAUDE.md`. If `your-setup/` still contains `{{REPLACE_ME}}` or
`<!-- SETUP_INCOMPLETE -->`, STOP and tell the user to run `/setup` first.

**If setup is complete (no markers found), the gate has done its job. Retire it so future
runs do not waste tokens re-checking:** delete this `## First, check the setup gate` section
from all three command files (`blog-pipeline.md`, `update-pipeline.md`, `llms-brand-page.md`)
and delete RULE 1 from `CLAUDE.md`. Do this once, then continue with the run.

## How to build it: invoke existing skills, do not improvise

Reuse the skills the engine already has. For each step, **invoke the named skill with the
Skill tool** and use its output. Do not redo their work from memory.

1. **Read `your-setup/`.** Take positioning and audience from `brand-and-voice.md`, and the
   offer, features, use cases, and decision factors from `your-offer.md`. This is the source
   of truth for what is real.
2. **Invoke `your-reference`.** Pull the user's strongest positioning, proof points, named
   customers, and key claims from their existing content, so the page reflects how they
   actually describe themselves.
3. **Invoke `answer-engine-audit` in brand mode.** Capture how ChatGPT, Perplexity, and AI
   Overviews describe the brand today: what is accurate, what is outdated, what is missing or
   wrong, and which competitors appear instead. This is the gap the page needs to close.
4. **Assemble the page.** Write a clear, extractable brand page with:
   - A one-paragraph summary of who the user is and who they serve.
   - Key points and differentiators (what only they can claim).
   - Decision factors a buyer weighs: integrations, pricing model, support, security and
     compliance, use-case fit.
   - A short, honest comparison framing versus the main alternatives.
   - Company facts: founding, location, notable customers, and similar.
   Use plain, self-contained statements an answer engine can quote. No marketing fluff.
5. **Invoke `verify-claims`.** Every company fact and competitor reference must have a real,
   retrievable source, or be cut. Accuracy is the entire point of this page.

## Output

Write to `content/llms-brand-page/brand-page.md`. Tell the user to publish it on a public
`/about` page (or a similar real, crawlable page on their site) so answer engines can read
it. Note that they should refresh it whenever the offer or positioning changes.

Never invent facts or sources. Never use em dashes.
