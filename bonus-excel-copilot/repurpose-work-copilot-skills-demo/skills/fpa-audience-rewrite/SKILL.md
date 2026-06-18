---
name: fpa-audience-rewrite
description: Rewrite finance and FP&A analysis (variance commentary, monthly close findings, forecast notes, budget-vs-actual writeups) for a specific stakeholder audience — CFO, board, department head, or accounting team. Use this skill whenever the user wants to take an existing analytical writeup and reframe it for a different reader, or asks to "rewrite this for the CFO," "reformat this for our department heads," "make this board-ready," or anything where the underlying numbers stay the same but the framing, level of detail, and tone need to shift. Always trigger when the user pastes or references a variance analysis, close memo, or finance commentary and mentions a different audience.
---

# FP&A Audience Rewrite

The same set of numbers needs to land very differently for a CFO than for a department head. CFOs want decisions; department heads want context for their own line; the board wants the strategic picture; accounting wants accuracy. This skill takes a single piece of finance analysis and rewrites it for the requested audience.

## When to use

The input is an existing analytical writeup (variance commentary, close findings, forecast notes, etc.) and the user wants the same content expressed for a specific audience. Don't use this skill to *create* the underlying analysis — only to reframe analysis that already exists.

## Optional input: underlying data

The user may provide the underlying data alongside the writeup (e.g., a variance xlsx, a headcount xlsx). Treat the writeup as the **primary input** — its narrative, hypotheses, and asks are what gets repurposed. Treat any provided data as a **fact-check source** for numbers that appear in the rewrite. If a number in the writeup conflicts with the data, prefer the data and flag the discrepancy in the output. Don't introduce new analyses or numbers from the data that aren't in the writeup.

## How to think about audience

Each audience cares about different things and reads at different levels of detail. Match all four levers below to the audience.

| Audience        | Wants                                          | Length        | Tone             | Detail level                           |
| --------------- | ---------------------------------------------- | ------------- | ---------------- | -------------------------------------- |
| CFO             | Decisions, risks, asks                         | Tight, ~250w  | Direct, peer     | Material variances only, with cause    |
| Board           | Strategic picture, performance vs commitment   | Tight, ~200w  | Confident        | Aggregate trends, no line-item detail  |
| Department head | What it means for *their* line, what's needed  | Medium, ~300w | Collaborative    | Their dept only, plus relevant context |
| Accounting team | Accuracy, classifications, reconciliation      | Medium, ~300w | Precise, factual | All variances, GL refs preserved       |

## Output structure

Always preserve the underlying numbers exactly — the same $60K Eng salary favorability is the same $60K regardless of audience. What changes is which numbers get airtime, what gets cut, and how cause and consequence are framed.

Use this structure as a starting point and adapt:

1. **One-line headline** — what this rewrite is about, in the audience's language
2. **What matters** — the 2–4 things this audience needs to know
3. **Cause / context** — why those numbers are what they are
4. **Asks or implications** — what the reader should do or watch for next

For the CFO and board audiences, lead with the headline number and the implication. For the department head, lead with what their line did and why. For accounting, lead with the variance facts and any reconciliation flags.

## Things to cut, things to keep

Across all audiences, ruthlessly cut:
- Internal process notes ("waiting on a JE to post")
- Hedging language ("appears to," "may indicate")
- Working-doc artifacts ("see attached")

Always keep:
- The actual dollar figures and percentages
- The cause behind each material variance
- Anything that requires a decision

For non-CFO audiences, additionally cut detail that isn't relevant to that reader. A department head reading the rewrite should not see other departments' line items unless they directly affect theirs.

## Examples

**Example 1 — CFO rewrite of a variance memo**
Input: a 700-word working-notes doc with five material variances, hypotheses, and open items.
Output: a ~250-word memo that opens with "March OpEx ran $66K unfavorable on a $2.1M base — and run-rate is meaningfully worse than that once timing items normalize." Lists the three biggest variances with their drivers. Closes with two specific asks (CMO confirmation on Q2 programs, VP Eng meeting to true up cloud).

**Example 2 — Department head rewrite for VP Engineering**
Input: same 700-word doc.
Output: a ~300-word note focused only on Engineering. Calls out the $60K salary favorability as timing (not run-rate savings), flags the $15K cloud overrun and proposes a true-up meeting, and notes the three open reqs. Does not mention Marketing, Sales, or G&A variances.

## Anti-patterns

- Don't change the numbers, even to "round for clarity." If the source says $35K, the rewrite says $35K.
- Don't add new analysis. If the source doesn't include attribution data, the rewrite shouldn't speculate.
- Don't pad. Each audience version should be shorter than the source unless the source is already thin.
- Don't strip cause. Every material variance should still have its driver in one sentence, even in the shortest CFO version.

## Asking for clarification

If the user names an audience that isn't in the table above (e.g., "rewrite this for our investors" or "for the audit committee"), ask one clarifying question about what the reader cares about and what the use is, then proceed.
