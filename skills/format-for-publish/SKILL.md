---
name: format-for-publish
description: Produce the final, publish-ready version of an article. Default is a clean document for copy-paste. If the user has connected a CMS, can publish straight to it as a draft.
---

# Format for publish

Hand the user the finished article in the form they can actually use.

## Input

The approved draft: `content/6-drafts-cited/{slug}.md` (or whichever draft the user signed
off on).

## Choose the output based on the CMS setting

Read `your-setup/cms-connection.md`:

### Default: clean copy-paste document (works for everyone)

Produce a tidy version ready to paste into any editor: correct heading levels, formatted
lists and tables, working links, and image placeholders marked where visuals go. Save it to
`content/8-publish/{slug}.docx` (or `.md` if the user prefers). This needs no setup and is
the right choice unless the user has connected a CMS.

### Format for answer-engine extraction

Whichever target you use, structure the final copy so AI Overviews and answer engines can
parse and cite it: clear question-shaped or claim-shaped headings, a short summary or
key-takeaways block near the top, real tables for comparisons (not images of tables), and
a concise FAQ where it fits the topic. Offer to add structured-data hints (FAQ or article
markup) if the user's CMS supports them. Do not stuff or over-format: clarity is the goal.

### If a CMS is connected (`status: connected`)

Use the connected CMS (WordPress, Webflow, or another via its MCP or API) to create the
article as a **draft, never published live**. Map headings, body, links, and any CMS-specific
formatting (for example WordPress blocks or shortcodes) correctly. Then give the user the
link to review and publish it themselves inside their CMS.

## If the user wants to connect a CMS now

If they ask to publish straight to their site but `cms-connection.md` says it is not set up,
walk them through connecting it (point to `docs/troubleshooting.md`), update
`cms-connection.md` to `status: connected`, then publish the draft.

## Always

Never publish live without the user explicitly asking. Default to creating a draft they
approve. Never use em dashes in the final copy.
