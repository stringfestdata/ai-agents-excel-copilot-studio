---
name: fpa-to-deck-outline
description: Turn FP&A analysis (variance commentary, monthly close findings, forecast notes, budget-vs-actual writeups) into a slide-ready deck outline with speaker notes — the kind used in a monthly business review, finance review, or close meeting. Use whenever the user wants to "turn this into slides," "build a deck from this," "make this presentation-ready," "prep for the monthly review," or any request that takes finance analysis and converts it into a slide outline. Always trigger when the input is finance analysis and the requested deliverable is a deck, slides, or presentation — even if the user doesn't say "skill" and even if they don't specify slide count.
---

# FP&A → Deck Outline

A monthly variance review deck is mostly the same shape every month: cover, headline, performance against plan, material variances, forward look, asks. This skill takes finance analysis and produces a slide-by-slide outline with titles, body content, and speaker notes — ready to drop into a deck template.

## When to use

The input is finance analysis. The output is a slide outline. If the user wants an email or memo, don't use this skill — use `fpa-to-cfo-email` or `fpa-audience-rewrite` instead.

## Optional input: underlying data

The user may provide the underlying data alongside the writeup (e.g., a variance xlsx). The writeup is the **primary input** — its findings, drivers, and forward-look points are what shape the slides. Provided data is a **fact-check source** for any number on the slides and is also useful when describing the table on the "Material variances" slide (e.g., to confirm the row sort order or pull headcount context). If a number in the writeup conflicts with the data, prefer the data and flag it. Don't introduce numbers from the data that the writeup didn't surface.

## Standard structure

A monthly variance review fits into 6–8 slides. Use this structure unless the user asks for something different. The structure exists because monthly reviews follow a predictable arc — anchor on plan, explain variances, look forward, close on decisions.

```
Slide 1 — Cover
Slide 2 — Headline / TL;DR
Slide 3 — OpEx vs Plan (the picture)
Slide 4 — Material variances (the table)
Slide 5 — Variance commentary — favorable
Slide 6 — Variance commentary — unfavorable
Slide 7 — Forward look / forecast implications
Slide 8 — Asks and decisions
```

If there are only 1–2 favorable and 1–2 unfavorable variances, collapse slides 5 and 6 into a single commentary slide. If there are more than three asks, keep slide 8 — don't try to bury asks in earlier slides.

## What goes on each slide

For each slide, produce:
1. **Slide title** — a full sentence statement of the takeaway, not a topic label
2. **Body content** — bullets, a table description, or a chart description (with the data needed to build it)
3. **Speaker notes** — what the presenter actually says, in plain prose, ~60–90 seconds per slide

### Title rules

Slide titles should make a point, not name a topic. The audience should be able to flip through the deck reading only titles and follow the story.

- Bad: "March Variance"
- Bad: "Engineering Spend"
- Good: "OpEx came in $66K unfavorable, but run-rate is meaningfully worse once timing reverses"
- Good: "Engineering salary favorability ($60K) is timing — three open reqs will close in Q2"

If you can't write a sentence-statement title for a slide, the slide probably doesn't have a point and should be cut.

### Body content rules

For each slide, body content is one of three types:

- **Bullets** (3–5 max): For commentary slides. Each bullet is the number + cause + implication, same shape as the email skill.
- **Table description**: For the material variances slide. Describe the table — columns, rows, formatting (e.g., "Department, Line Item, Budget, Actual, Variance, Variance % — sorted by absolute variance descending, color-code unfavorable variances red").
- **Chart description**: For OpEx vs Plan slides. Describe the chart — chart type, axes, data, what to highlight (e.g., "Horizontal bar chart, departments on Y-axis, two bars per department for Budget and Actual, callout for the largest variance").

Don't try to render the chart or table — describe it precisely enough that the deck builder (human or another tool) can build it.

### Speaker notes rules

Speaker notes are plain prose, the way the presenter actually talks. They should:
- Restate the title takeaway in different words
- Walk through the body content in order
- Add one piece of context the slide doesn't already show (e.g., "this is the third month in a row Marketing programs has been over plan")
- End with a transition into the next slide

Aim for 60–90 seconds of spoken material per slide. Roughly 100–150 words.

## Example — a single slide done right

```
Slide 4 — Material variances

Title: "Five line items moved by more than $10K — three are timing, two are forward risks"

Body (table description):
Build a 5-row table with columns: Department, Line Item, Budget, Actual, Variance ($), Variance (%), Driver.
Rows, sorted by absolute variance descending:
1. Engineering, Salaries & Benefits, 880K, 820K, -60K, -6.8%, Open reqs (timing)
2. Marketing, Marketing Programs, 120K, 180K, +60K, +50%, Q1 pipeline push
3. G&A, Professional Services, 50K, 85K, +35K, +70%, Audit + legal
4. Engineering, Software & SaaS, 60K, 75K, +15K, +25%, Cloud / ML workloads
5. Sales, Travel & Entertainment, 30K, 45K, +15K, +50%, EMEA prospect, in-person QBR

Color: unfavorable variances in red, favorable in green.

Speaker notes:
"Five line items had material variances this month — anything over fifteen thousand dollars or twenty percent. Three of them are timing-driven and will normalize: Engineering salaries from open reqs, Marketing programs from a pull-forward decision, and the audit fees in G&A which were a one-time scope expansion. Two of them are forward risks: the cloud spend in Engineering, which reflects ML workloads moving to production, and Sales T&E, which is likely to repeat as we lean further into EMEA. We'll come back to both of those in the forward look. The headline takeaway: don't read the sixty-six thousand unfavorable aggregate as run-rate either — once Engineering salary timing reverses in Q2, run-rate is closer to one-twenty-five unfavorable per month."
```

## Anti-patterns

- Topic-label titles ("March Variance," "Engineering Spend") instead of sentence-statement titles.
- Trying to fit every line item onto a slide. If something isn't material, it's a footnote or it's cut.
- Speaker notes that just repeat the bullets verbatim.
- Adding an "Appendix" slide that's actually the same content as earlier slides. If it's important, it goes earlier; if it's not, cut it.
- Producing the deck file itself instead of the outline. This skill stops at the outline — building the .pptx is a separate step.

## Output format

Produce the outline as markdown, with each slide as a level-2 heading, body content under it, and speaker notes in a clearly labeled section. Don't produce a .pptx file. The outline should be ready for a human (or another skill) to assemble into a deck template.
