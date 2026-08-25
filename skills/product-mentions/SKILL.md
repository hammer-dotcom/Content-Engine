---
name: product-mentions
description: Annotate an outline with honest, in-context places to mention what the user sells, so the draft includes the product naturally instead of as a forced plug.
---

# Product mentions

Find where the user's offer genuinely belongs in this article. Done as its own step so it
happens reliably and never gets shoehorned in during drafting.

## Input

- Outline: `content/3-outlines/{slug}.md`
- The user's offer: `your-setup/your-offer.md` (features, use cases, and how aggressively
  to mention it: light, medium, or heavy).

## How to run

1. Read the outline section by section.
2. For each section, ask: is there a point where this user's product or feature is the
   honest, useful answer to what the reader is dealing with right here?
3. **Anchor mentions to decision factors, not features.** B2B buyers and answer engines both
   weigh the same things: integrations, pricing model, support, security and compliance,
   onboarding, and fit for a use case. Frame a mention around the decision factor it speaks
   to ("if you need SOC 2, here is how X handles it"), not a bare feature plug. This is also
   what makes the mention quotable by an answer engine summarising the category.
4. Respect the aggressiveness setting. Light means only the obvious spots. Heavy means
   weave it through wherever it truly fits. Never force a mention where it does not help
   the reader: a forced plug costs more trust than it gains.
5. For each genuine spot, add a signpost noting which feature or decision factor to mention
   and the angle.

## Output

Write the outline plus the annotations to `content/4-outlines-annotated/{slug}.md`. Each
product signpost should be clearly marked so the `draft` step knows to act on it. If a
section has no honest place for a mention, leave it alone and say so.
