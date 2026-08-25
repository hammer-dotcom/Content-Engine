---
name: voice-of-customer-mining
description: Mine voice-of-customer material (sales calls, customer interviews, win/loss calls, support tickets, survey responses, review comments) for high-intent topics, real buyer language, pain points, and objections. Use early in content creation, or on its own to refresh the topic backlog.
---

# Voice-of-customer mining

The single strongest source of B2B content ideas is not a keyword tool. It is the language
your customers use when they describe their problems. Keyword tools sort everything by
volume, so everyone chases the same terms. Voice-of-customer material surfaces the ultra
long-tail, high-intent topics and the exact phrasing competitors never find.

## Input

Whatever is in `inputs/voice-of-customer/`. This can be a mix of:

- Sales calls and discovery call transcripts
- Customer interviews and win/loss calls
- Support tickets and chat logs
- Survey open-ended responses
- Review-site comments (yours or competitors')

Transcript exports from Gong, Fireflies, Otter, Zoom, or plain text all work.

## If the folder is empty

Do not fail silently. Tell the user, then continue without it:

> I didn't find any voice-of-customer material in `inputs/voice-of-customer/`. For B2B, this
> is the best source of high-intent topics and the exact language your buyers use: sales
> calls, customer interviews, win/loss calls, support tickets, survey responses, review
> comments. Drop any of those in that folder before your next run and I'll mine them.

Explain how (export a transcript, drop the file in), and note the folder contents stay local
and are not pushed. Then hand control back so the pipeline can carry on.

## Steps

1. Read everything in the folder. Handle each type for what it is: a call transcript reads
   differently from a one-line support ticket or a survey answer.
2. Pull out, with the source noted for each:
   - **Pain points** in the customer's own words.
   - **Objections and hesitations** (the "what if our employees find out" type concern).
   - **Decision factors** they raise (integrations, pricing, compliance, support, fit).
   - **Verbatim phrases** worth using as headers or keywords. Keep the real wording.
   - **Questions** they ask that map to high-intent, low-competition topics.
3. Group these into themes and reverse-engineer each into a candidate topic or keyword,
   noting the funnel stage (most will be mid to bottom).
4. Do not invent quotes. Use only what is in the material. If something is paraphrased, say so.

## Output

- When run inside `/blog-pipeline` for a keyword: write the topic-relevant findings to
  `content/0-voice-of-customer/{slug}.md` for `research` to use.
- When run on its own: write a `content/0-voice-of-customer/backlog.md` with the candidate
  topics and themes, and offer to add the strongest to `content/keyword-ideas.csv`.
