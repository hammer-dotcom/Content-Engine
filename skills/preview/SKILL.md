---
name: preview
description: Turn a draft into a clean, styled HTML page that opens in the browser, so the user can read the article as it will look rather than as raw markdown.
---

# Preview

Let the user read the article the way a reader would. Reviewing raw markdown is unpleasant
and hides problems. A styled preview makes them obvious.

## Input

Cited draft: `content/6-drafts-cited/{slug}.md` (or the latest draft available).

## Steps

1. Convert the markdown draft to a single self-contained HTML file: headings, paragraphs,
   lists, tables, links, and image placeholders all rendered.
2. Style it simply and readably: a comfortable reading width, clear type, sensible spacing.
   Keep all the CSS inline in the one file so it works with no internet and no other files.
3. If `your-setup/` defines brand colours or fonts, apply them lightly so it feels like the
   user's site. Do not over-design. The point is to read the words.
4. Show any claims that `verify-claims` flagged as a small note at the top, so the user
   does not miss them.
5. **Citation-readiness check.** Add a short note at the top flagging whether the article
   has passages an answer engine could lift as a clean, cited answer (a clear definition, a
   direct answer to the core question, a self-contained comparison). If those are weak, say
   so, so the user can tighten them before publishing.

## Output

Write the HTML to `content/7-preview/{slug}.html` and tell the user the path so they can
open it in their browser. On most machines they can run `open` (Mac) or `start` (Windows)
on the file, or double-click it in VS Code's file list.

Offer to format it for publishing next with `format-for-publish`.
