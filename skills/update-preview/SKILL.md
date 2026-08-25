---
name: update-preview
description: Build a single HTML preview that shows the entire refreshed article in full, with every change marked inline, so the user can read the whole new piece and see exactly what changed on one page.
---

# Update preview

Show the user the complete refreshed article, not just the changes. They need to read the
whole new piece top to bottom AND see what changed, on the same page. A diff of fragments
alone hides how the article actually reads now.

## Input

- Original: `content/updates/1-extracted/{slug}.md`
- Updated: `content/updates/7-updated-draft/{slug}.md`

## Steps

1. Build a single self-contained HTML file that renders the **entire refreshed article**,
   in full, top to bottom, exactly as it will read once published. The unchanged parts are
   shown as normal body text, not hidden or summarised.
2. **Mark the changes inline, in place, within that full article:**
   - New or added text and new sections: highlighted (for example a light green background).
   - Replaced facts or stats: show the new value highlighted, with the old value struck
     through next to it so the change is visible in context.
   - Removed text: struck through, kept visible so the user sees what was cut.
   Use a small colour key at the top so the marks are obvious.
3. Add a short **summary of changes** at the very top (a few bullets: what was updated and
   why), then the full marked-up article below it. The summary is a quick orientation, the
   full article is the main view.
4. For each changed stat, show its source next to it so the user can sanity-check.
5. Keep all CSS inline so the file opens with no internet and no other files.
6. Apply the user's brand colours lightly if defined, but keep readability first. The
   change-highlight colours must stay distinct from brand colours so marks are never missed.

## Output

Write to `content/updates/5-update-preview/{slug}.html` and give the user the path to open
it. Remind them: nothing is published until they say so. Once they approve, they can run
`format-for-publish` to produce the final version or push a draft to their CMS.
