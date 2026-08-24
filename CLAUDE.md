# CLAUDE.md

This file tells Claude Code how to behave inside this repository. Read it at the start
of every session and follow it.

## What this repository is

A personal content engine. It turns a keyword or an existing URL into a publish-ready
article by working through a chain of small, single-purpose skills. Each skill saves its
output to a file so the human can review and fix any single step.

There are two pipelines:

- **Creation:** `/blog-pipeline "keyword"` runs research through preview for a new article.
- **Update:** `/update-pipeline "url"` refreshes an article the user already published.

## RULE 1: The setup gate (check this before doing any content work)

This repo ships with placeholder brand, voice, and product files. They are useless until
the user personalises them.

**Before running `/blog-pipeline`, `/update-pipeline`, or any individual content skill,
you MUST check whether setup is complete:**

1. Look in the `your-setup/` folder.
2. If any file there still contains the token `{{REPLACE_ME}}` or the line
   `<!-- SETUP_INCOMPLETE -->`, setup is NOT done.
3. If setup is not done, STOP. Do not run the skill. Say this to the user:

   > Before I can write content that sounds like you, you need to personalise this engine.
   > Run `/setup` and I will walk you through it. It takes a few minutes.

4. Only proceed once those markers are gone from every file in `your-setup/`.

Never run a content skill against placeholder brand data. The whole point of the gate is
to stop the engine writing in a generic or borrowed voice.

This is a first-run safeguard only. Once setup is confirmed complete, the content commands
will retire their gate-check sections and delete this rule so future runs do not waste
tokens re-checking. That is expected: do not re-add it.

## RULE 2: Read the user's setup before writing

Once the gate is open, treat these files as the source of truth:

- `your-setup/brand-and-voice.md` — voice, tone, rules, do and do not.
- `your-setup/your-offer.md` — what the user sells, for natural product mentions.
- `your-setup/voice-examples/` — the user's best articles. Infer their voice from these.
- `your-setup/data-sources.md` — which data tools are turned on (see Rule 3).

The voice examples outrank everything. When in doubt about tone, match the examples, not
abstract rules.

## RULE 3: Data sources are toggleable

`your-setup/data-sources.md` lists which tools the user has connected. The default is
**built-in web search and fetch**, which works for everyone with no setup.

If a tool is marked `on` (for example Google Search Console MCP, DataForSEO MCP, GA4),
prefer it for that kind of data. If it is marked `off`, use the built-in web fallback and
do not pretend you have data you cannot get. Never invent keyword volumes, traffic numbers,
or metrics. If you cannot retrieve a number, say so.

## RULE 4: Save every step

Every skill writes its output to a file in `content/` (or `content/updates/` for the
update flow), named with the article's slug. Do this even when running the full pipeline.
It is what lets the user find and fix the one step that went wrong.

## RULE 5: The CMS reminder

`your-setup/cms-connection.md` records whether the user has connected a CMS (WordPress,
Webflow, etc.) for publishing, and the date they were last asked.

At the start of a session, if that file says the connection is deferred (`status: later`)
and it has been **seven or more days** since `last_prompted`, ask once:

> You chose to set up your CMS connection later. Want to do it now so I can publish
> straight to your site? If not, no problem, I will check again next week.

Then update `last_prompted` to today's date whether they say yes or no. Do not nag more
than once a week.

## Writing standards

These are sensible defaults. The user's `brand-and-voice.md` overrides them.

- Write in plain, direct language. Short sentences. Active voice.
- **Never use em dashes.** Restructure the sentence with a comma, full stop, or colon.
- Do not invent statistics, sources, or quotes. Cite real, retrievable sources only.
- Lead with the most useful point first. Do not bury it.
- One clear call to action per article.

## The "average of the internet" test (apply to every draft)

The point of this engine is not to publish faster. It is to publish things worth reading.
Before any article is called done, ask: could the reader get this same piece by typing a
one-line prompt into ChatGPT or Google? If yes, it is not worth publishing. A draft that is
just the consensus, with no original data, point of view, customer language, or specific
example, has failed the test. Push it back toward the proprietary inputs (`your-reference`)
and the voice-of-customer material until it says something only this user could say.

## Write for answer engines, not just rankings

Buyers increasingly read a synthesised answer from ChatGPT, Perplexity, or Google AI
Overviews instead of clicking ten links. So across outline, draft, and format, structure
content to be understood and **cited**: clear question or claim-shaped headers, a quotable
self-contained answer at the start of each section, real comparison tables, and accurate
product facts. Getting cited and represented accurately matters as much as ranking. Do not
treat a traffic dip alone as failure: influence and citations count too.

## Make it yours

The user is encouraged to fork and change this repo: rename skills, add or remove steps,
change data sources. If they ask to modify the pipeline, help them edit the relevant
`SKILL.md` file rather than working around it.
