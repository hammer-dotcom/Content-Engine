---
name: visuals
description: Suggest images, screenshots, or diagrams for an article and where they go. Off by default. Turn on in data-sources.md once you have a way to capture or generate visuals.
---

# Visuals

Suggest the images an article needs. This step is optional and is **off by default**, since
good automated visuals are still hard. Honest screenshots beat decorative stock images.

## When this runs

Only when `visuals` is marked on in `your-setup/data-sources.md`, or the user asks for it
directly. The `/blog-pipeline` command skips it otherwise.

## Input

Cited draft: `content/6-drafts-cited/{slug}.md`.

## Steps

1. Read the draft and find the points where a visual would genuinely help the reader: a
   step that is easier shown than told, data better seen as a chart, a process worth a
   diagram.
2. For each, write a clear spec: what the visual should show, what type it is (screenshot,
   chart, diagram), and exactly where it goes in the article.
3. If the user's offer involves a tool or product (`your-setup/your-offer.md`), and a
   screenshot of it would help, describe the specific screen to capture.
4. **Prefer original, proprietary visuals.** An honest screenshot of the user's own product
   or results, or a chart of their own data, is a differentiator a competitor cannot copy.
   It beats a generic stock image or a diagram of common knowledge. Favour these.
5. Do not fabricate a chart from invented data. Only chart numbers that are real and sourced.

## Output

Write the visual specs to `content/images/{slug}/specs.md`, and create the folder for the
user to drop the actual image files into. Capturing or generating the images stays a human
step in v1 unless the user has wired up a screenshot or image tool.
