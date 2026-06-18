---
name: fpa-variance-commentary
description: Generate first-pass FP&A commentary from raw variance data — the kind of working-notes writeup an analyst produces after the close, before any audience-specific reformatting. Use this skill whenever the user has a variance file (Budget vs Actual at the line-item level, usually in Excel or CSV) and wants commentary on it. Trigger on phrases like "write up the variance," "commentary on March numbers," "what stands out in this variance file," "write me a variance writeup," "analyze this budget vs actual," or any request that takes raw FP&A data and asks for narrative analysis. Always trigger when the input is a variance dataset and the desired output is prose commentary, even if the user doesn't say the word "commentary."
---

# FP&A Variance Commentary

This skill takes raw variance data — a Budget-vs-Actual file with line items — and produces the working-notes-style commentary that an FP&A analyst writes after the close. It's the first step in the repurposing chain. The output of this skill becomes the input to downstream skills like `fpa-audience-rewrite`, `fpa-to-cfo-email`, and `fpa-to-deck-outline`.

## When to use

The input is a tabular variance dataset (Department × Line Item with Budget, Actual, Variance, and ideally Variance %). Optional supporting data — headcount, prior-period actuals, forecast — sharpens the commentary but isn't required.

The output is a working-notes markdown writeup with the structure below. It's deliberately not audience-specific. It's the "raw fact pattern with hypotheses" stage. Audience-shaping happens later via downstream skills.

## What "first-pass commentary" actually means

Commentary in FP&A is not a list of variances. A list is what the variance file already gives you. Commentary is a list of variances + cause + implication, written in the language of the business, with timing-vs-run-rate distinctions called out, decisions surfaced, and open items flagged. The reason FP&A analysts can't just hand the variance file to leadership is that the file is data, not narrative — and the narrative is the part that requires judgment.

The skill captures the judgment that gets repeated every month so the analyst doesn't have to re-explain "what good commentary looks like" to the model on every close.

## Output structure

Always use this structure, in order. The structure is the value of the skill.

```
# [Period] Variance Analysis — Working Notes

**Author:** FP&A team
**Status:** Internal working draft — not for distribution
**Period:** [period and quarter context]

[One-line provenance: where the numbers came from, as-of date.]

## Headline

[2–4 sentences. Aggregate variance ($ and %). What the aggregate hides. Run-rate point if applicable.]

## Material variances ([threshold])

[For each material variance, in this exact pattern:]
**[Department] [Line Item] — [favorable/unfavorable] [$X] ([+/-Y%]).** [One paragraph: cause, context, timing-vs-run-rate, what should be watched.]

## Smaller variances worth noting

[Bullet list of sub-threshold variances that still warrant a sentence each.]

## Headcount

[If headcount data is provided. Total budgeted vs actual, where the gap is, expected normalization.]

## Themes and hypotheses

[Numbered list of 2–4 thematic observations that span multiple variances. The "what does this all mean together" layer.]

## Decisions / asks

[Bullet list of specific decisions or asks for the next review. Each ask names the owner if known.]

## Open items

[Reconciliation flags, late JEs, anything that could shift the numbers slightly. Material vs immaterial called out.]
```

## How to identify "material" variances

Default threshold: anything more than $10K in absolute dollar variance OR more than 20% in percentage variance. Use the user's threshold if specified.

When you call something material, you owe the reader a cause. If the data and any provided context don't support a confident cause, write "cause unknown — flagged for follow-up" rather than speculating. False causes are more harmful than missing causes.

## How to write the cause/context paragraph

Each material variance gets one paragraph with these elements, in roughly this order:

1. **The number.** Restate dollars and percent in a sentence (the heading already shows them, but readers skim).
2. **The driver.** What caused this? Use any context the user provided (headcount data, prior conversations, embedded notes in the variance file). If the variance is multi-part, name each part with its dollar share.
3. **Timing vs run-rate.** Critical for FP&A. Will this reverse next month? Is it permanent? Will it grow? This is what separates a commentary writer from a commentary parser.
4. **Implication or what to watch.** Forward-looking. If timing-driven, note the expected reversal period. If permanent, note that it should be reflected in the forecast.

## Writing voice

Working notes voice. This is not a polished memo — it's the analyst's first organized thinking after the close. That means:

- Short, declarative sentences. Numbers prominent.
- It is OK to be tentative about causes when data is thin: "appears to be," "consistent with," "needs follow-up."
- It is OK to flag open items inline: "still posting as of the export."
- Full prose, not bullets, in the headline and per-variance sections. Bullets only for the asks and open items.
- Avoid hedging language in the headline ("seems," "may be"). Headlines should commit to a number.

This voice is intentionally **not** ready for the CFO. Polishing for the CFO is what the downstream `fpa-audience-rewrite` and `fpa-to-cfo-email` skills do. Don't pre-polish here — it makes the downstream skills work harder.

## Optional input: supporting context

If the user provides additional context alongside the variance data — headcount, prior-period actuals, business notes from leadership, decisions made in-quarter — use it to sharpen the cause statements. Without context, the model can identify *that* there's a $60K Engineering salary favorability but not *why*. With headcount data showing 3 open reqs, the cause becomes obvious.

When context is missing, the commentary will be thinner but should still be honest. Better to write "cause not visible from data; recommend confirming with VP Eng" than to invent a story.

## Anti-patterns

- **Don't restate the variance file.** A bullet list of every line item is not commentary. Pick the material ones, group similar ones, and tell a story.
- **Don't bury the headline.** Aggregate number + run-rate point in the first paragraph. If the aggregate is misleading on a run-rate basis, say so in the headline, not on page 3.
- **Don't speculate causes.** "Cloud spend is up — likely due to AI workloads" without supporting data is a guess dressed up as analysis. Either support it or flag it as unknown.
- **Don't pre-tailor for an audience.** This is working notes, not a CFO memo. Length, density, and language should match the working-notes register. Audience tailoring is the next skill's job.
- **Don't skip the asks section.** Every commentary ends with what needs to happen next. If nothing requires a decision, write "No asks this period" — but think about it before writing that.

## Output format

Produce the commentary as a single markdown document, ready to be saved as a `.md` file or pasted into a working notes tool. No commentary around the commentary — just the document itself.

## Example

**Input:** A March variance xlsx with 25 line items across 5 departments, plus a headcount file showing 3 open Engineering reqs and a 1-person Sales gap.

**Output:** A ~700-word markdown writeup that:
- Opens with "OpEx came in at $2,203K against a budget of $2,137K — unfavorable $66K (3.1%). Run-rate is closer to $125K unfavorable per month once timing items normalize."
- Calls out 5 material variances (each over $10K or 20%): Engineering Salaries favorable $60K (timing — open reqs), Marketing Programs unfavorable $60K (Q1 pipeline push), G&A Professional Services unfavorable $35K (audit + legal), Engineering Software unfavorable $15K (cloud / ML), Sales T&E unfavorable $15K (EMEA, in-person QBR).
- Includes 2–3 thematic observations: timing vs run-rate, in-quarter spend not flowing into forecast, cloud as a forward risk.
- Closes with 3–4 specific asks naming owners (CMO on Q2 programs, VP Eng on cloud true-up, etc.).
- Notes open items: BambooHR vs Workday headcount reconciliation, late JEs.
