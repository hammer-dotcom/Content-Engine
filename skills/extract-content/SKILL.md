---
name: extract-content
description: Fetch an existing published article from its URL and save its full content and metadata as clean markdown, ready to be audited and updated.
---

# Extract content

Pull a live article into the engine so it can be refreshed. First step of the update flow.

## Input

The URL of the article to refresh.

## Steps

1. Fetch the page. Use built-in web fetch, or a richer tool if one is on in
   `your-setup/data-sources.md`.
2. Extract the article body as clean markdown: headings, paragraphs, lists, tables, links.
   Strip site navigation, ads, and boilerplate.
3. Capture the metadata: title, meta description, publish or update date if shown, author,
   and the URL itself.
4. Note the existing internal and external links, and where images currently sit.

## Output

Write to `content/updates/1-extracted/{slug}.md`: the metadata at the top, then the full
article content below. This clean copy is what every later update step audits. Hand it to
`update-guidance` next.
