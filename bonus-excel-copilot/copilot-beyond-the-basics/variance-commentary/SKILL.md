---
name: variance-commentary
description: Writes budget-versus-actual commentary for a monthly or quarterly location P&L. Use this when a worksheet contains budget and actual figures side by side and the user asks for variance commentary, a variance narrative, or an explanation of what moved against plan. Applies a fixed materiality threshold and a fixed house writing standard.
metadata:
  version: 1.0.0
  tags: excel
---

# Variance commentary

You are writing the variance section of a monthly operating review for a multi-location
restaurant group. The audience is general managers and the finance lead. They already know
the business; they do not need the metrics defined.

## What to do

1. Find the table containing budget and actual figures. Confirm it has, at minimum, a period, a budget amount, and an actual amount.
2. Calculate variance as actual minus budget, and variance percent as variance divided by
   budget. A negative variance is unfavorable.
3. Identify every variance that clears the materiality threshold below.
4. Write one comment per material variance, ordered from largest unfavorable to largest
   favorable.
5. Close with a two-sentence summary of the period overall.

## Materiality threshold

A variance is material if it is greater than **$5,000** in absolute dollars **or** greater
than **10%** of budget — whichever of the two is met first. Do not comment on anything below
both thresholds, however interesting it looks.

## Writing standard

- State the driver before the number. "Reduced sushi service at Navy Yard cut sushi revenue
  $14,200 below plan" — not "Sushi was $14,200 under."
- Keep each comment under **40 words**.
- Round dollars to the nearest hundred. Show percentages to one decimal place.
- Use the location names exactly as they appear in the data.
- Write in plain past tense. No hedging verbs — "was," not "appears to have been."

## Common pitfalls to avoid

- **Do not speculate about causes.** If a cause is not stated in an attached document or in
  the workbook, write "driver not documented" and move on. Inventing a plausible reason is
  the worst thing this skill can do.
- Do not aggregate locations into regions or states.
- Do not net a favorable variance against an unfavorable one to make a category look calm.
- Do not restate the whole table. Commentary is the exception report, not the report.
- Do not claim to be finished if you could not read the budget or actual column.

## Workbook output

Write the commentary to a new worksheet named **Variance Commentary**:

- Row 1: a title with the entity and period.
- Column A: location. Column B: category. Column C: period. Column D: variance in dollars.
  Column E: variance percent. Column F: the comment.
- Format column D as currency with negatives in parentheses, and column E to one decimal
  place.
- Put the closing two-sentence summary two rows below the last comment, in column A.

Leave every existing worksheet untouched.
