---
description: Personalise the content engine. Walks the user through every placeholder, learns their voice from examples, and unlocks the pipeline.
---

You are running the guided setup for this content engine. Your job is to replace every
placeholder in `your-setup/` with the user's real information, learn their voice from
their example articles, and remove the setup markers so the pipeline unlocks.

Be warm and plain-spoken. The user may have never done anything like this. Confirm as you
go.

## Core principle: documents first, questions second

Do not start by interrogating the user. Most people already have material that answers
half of these questions: a brand guide, a tone of voice doc, an About page, an ICP or
persona file, a product one-pager, old briefs. Always try to **ingest what they already
have first**, extract everything you can, and only ask questions to fill the gaps and
confirm. Asking someone to retype information they already wrote down is the slow,
annoying path. Avoid it.

## Before you start

Read the current state of every file in `your-setup/` so you do not overwrite anything
the user already filled in. If setup was done before, treat this as an update: tell them
what is already set and ask what they want to change, rather than starting from scratch.

## Step 0: Ask what they already have

Before any detail questions, ask the user whether they have existing material that
describes their brand, voice, audience, or product. Give concrete examples so they know
what counts:

> Before I ask you anything, do you already have any of these written down somewhere?
> A brand or style guide, a tone of voice doc, an About page, an ICP or buyer persona,
> a product one-pager, past content briefs, anything like that.
>
> If yes, you can:
> - Drop the files into the `your-setup/source-docs/` folder, or
> - Paste me links (Google Docs, Notion, a live web page) and I will read them, or
> - Just tell me the file paths.
>
> If you do not have anything to hand, no problem, I will ask you a few questions instead.

Then:

- **If they provide documents or links:** read all of them. Pull out everything relevant
  to brand, voice, audience, words to avoid, hard rules, the offer, features, and use
  cases. Pre-fill the matching placeholder files from what you found. Then in each step
  below, show the user what you extracted and ask them only to confirm or correct it, plus
  fill anything that was genuinely missing from their docs.
- **If they have nothing:** fall back to the question flow in each step below.

Keep the original source files where they are. Do not delete anything the user shared.

## Step 1: Brand and voice basics

If you already extracted some of this in Step 0, show it back and ask the user to confirm
or fix it. Only ask outright about whatever is still missing:

1. Their brand name or their own name.
2. What they write about.
3. Who they write for.
4. Their voice in three words.
5. How they would describe their tone.
6. Any words or phrases they never want used.
7. Any hard formatting rules (the em dash ban is already in place).

Write the result into `your-setup/brand-and-voice.md`, replacing each `{{REPLACE_ME}}`.

## Step 2: Voice examples (the important one)

Explain plainly: "The best way for me to sound like you is to read your best writing.
Add 5 to 10 of your strongest articles to the `your-setup/voice-examples/` folder, or
paste me the links and I will fetch them."

Wait for them. Once examples exist (files in the folder, or links they gave you):

1. Read all of them.
2. Work out the patterns that make them theirs: how they open, sentence rhythm, how they
   use evidence and examples, structure, recurring phrases and moves, what they avoid.
3. Write what you found into the "Your voice examples" section of `brand-and-voice.md`,
   in concrete terms ("you open with a sharp claim, then back it with a specific number").
4. Read it back to the user and ask them to correct anything that does not feel right.
   Apply their corrections. This back-and-forth is the point: do not skip it.

If they have no examples yet, tell them the engine will work but will sound more generic,
and they should add examples as soon as they can. Do not block setup on this alone.

## Step 3: Your offer

If Step 0 turned up a product one-pager, sales page, or feature list, draft
`your-setup/your-offer.md` from it and show the user to confirm. Otherwise walk through it
with them: what they sell, key features, best use cases, and how aggressively to mention
it (light, medium, heavy). Either way, end by confirming the values with them before saving.

## Step 4: Data sources

Open `your-setup/data-sources.md`. Explain that the engine already works using built-in
web search, with no setup. Ask if they have any of these connected already (Google Search
Console MCP, DataForSEO MCP, GA4). For each one they have, set it to `on`. For the rest,
leave `off` and tell them they can connect them later. Do not make them feel they need any
of these.

## Step 5: CMS connection

Open `your-setup/cms-connection.md`. Explain: "By default I give you a clean document to
copy and paste. I can also publish straight to your CMS if you connect it. Want to set
that up now, or later?"

- If **now**: help them connect their CMS (WordPress, Webflow, or another via MCP or API).
  Point them to the troubleshooting doc for the connection steps. Set `status: connected`
  and `cms:` to their platform.
- If **later**: set `status: later` and `last_prompted:` to today's date. Tell them you
  will check in about once a week, and they can run `/setup` any time to do it.

## Step 6: Remove the markers and confirm

Once a file is fully filled in, remove its `<!-- SETUP_INCOMPLETE -->` line and make sure
no `{{REPLACE_ME}}` tokens remain in it. When every file in `your-setup/` is clean:

1. Do a final check across the whole `your-setup/` folder for any leftover markers.
2. Tell the user setup is complete and the engine is unlocked.
3. Show them their first command:

   > You are ready. Write your first article with:
   > `/blog-pipeline "your topic"`
   > Or refresh an existing one with:
   > `/update-pipeline "the url"`
   > And build your LLM brand page, so AI answer engines describe you accurately, with:
   > `/llms-brand-page`

Keep the tone encouraging. They just built their own content engine.
