---
name: fpa-to-cfo-email
description: Turn FP&A analysis (variance commentary, close findings, forecast notes, budget-vs-actual writeups) into a tight, CFO-ready email. Use whenever the user wants to "send this to the CFO," "draft an email to finance leadership," "summarize this for the CFO," or any request that takes finance analysis and converts it into an internal email. Always trigger when the input is a variance memo, close findings, or finance writeup and the requested deliverable is an email — even if the user doesn't say "skill," doesn't name the format precisely, or just says "send this up."
---

# FP&A → CFO Email

CFOs read a lot of email and have approximately 90 seconds for any given one. This skill takes a piece of finance analysis and produces an email that respects that time budget while still landing the things a CFO actually needs: the headline, the material variances, the cause, and the asks.

## When to use

The input is finance analysis (variance memo, close commentary, monthly review notes). The output is one email — subject line, opening, body, sign-off. If the user wants a deck, a memo, or anything other than an email, don't use this skill.

## Optional input: underlying data

The user may provide the underlying data alongside the writeup (e.g., a variance xlsx). The writeup is the **primary input** — its findings and asks are what get formatted into the email. Provided data is a **fact-check source** for any number that appears in the email. If the writeup says $66K unfavorable and the data confirms it, send the number with confidence; if there's a discrepancy, prefer the data and flag it. Don't introduce numbers from the data that the writeup didn't surface.

## Email structure

Always use this structure, in order. The structure is the value of the skill — don't deviate.

```
Subject: [Period] OpEx — [headline takeaway in 6–8 words]

Hi [name],

[Headline paragraph: 2–3 sentences. Lead with the aggregate number. Then the most important thing the CFO needs to take away — usually a run-rate or directional point that the aggregate hides.]

The material variances:

• [Variance 1]: [$ and %], [one-sentence cause]. [One-sentence so-what.]
• [Variance 2]: [$ and %], [one-sentence cause]. [One-sentence so-what.]
• [Variance 3]: [$ and %], [one-sentence cause]. [One-sentence so-what.]

[Optional one-paragraph forward look: what this means for the next quarter / forecast.]

Asks:
• [Specific ask 1, with the person who owns the decision.]
• [Specific ask 2.]

Happy to walk through any of this. Full working notes attached.

[Sign-off]
```

## Subject line rules

The subject line is the most-read part of the email. Make it specific and load-bearing.

- Bad: "March variance"
- Bad: "FYI — March numbers"
- Good: "March OpEx — $66K unfavorable, run-rate worse once timing reverses"
- Good: "March close — Marketing $60K over, three other variances to discuss"

Lead with the period and the headline takeaway. Include numbers in the subject when the takeaway is numeric.

## Headline paragraph rules

Two to three sentences, no more. The pattern that works:

1. **First sentence: the aggregate.** "OpEx came in at $2.20M against a $2.14M budget — unfavorable $66K (3.1%)."
2. **Second sentence: the thing the aggregate hides.** This is almost always a run-rate point, a timing point, or a forward risk.
3. **Optional third sentence:** the headline ask.

Never bury the lede. If the headline finding is "we have a Q2 cloud cost problem," the headline paragraph says so.

## Bullet rules

Three bullets is the sweet spot. Four is the maximum. If there are more than four material variances, group the smaller ones into a "smaller items" bullet and reference the working notes.

Each bullet has three parts and they go in this order:
- The number (dollars and percent)
- The cause (one sentence)
- The implication (one sentence — what does this mean going forward?)

Don't include a variance unless you can name a cause for it. "We don't know why" is fine to write — it just goes in the asks section.

## Asks rules

Every email ends with specific asks. An ask is something the CFO either has to decide or has to weigh in on. A status update is not an ask.

Bad ask: "Let me know your thoughts."
Good ask: "Do you want to re-baseline Q2 programs spend up by $40K, or hold it flat and risk a similar variance?"

Name the owner where there is one. "Need a 30 minutes with VP Eng to true up the cloud line — I can set it up if you want me in the room."

## Length

Target 200–300 words for the body. Strip anything that doesn't fit. If the source analysis has six material variances and forty-five total line items, the email still gets three bullets — the rest goes in the working notes attachment.

## Tone

CFOs are peers, not customers. Don't oversell, don't apologize, don't pad. Write the way a senior finance person writes to another senior finance person — direct, numerate, no preamble.

Don't write:
- "I hope this finds you well"
- "Just wanted to flag"
- "Let me know if you have any questions"

Do write:
- The headline number
- The cause
- The ask

## Anti-patterns

- Adding a "background" or "context" section before the headline. The headline *is* the context.
- Burying numbers inside paragraphs instead of putting them in bullets.
- Vague asks ("thoughts welcome") instead of specific ones.
- Using language from the source memo verbatim if it's working-notes flavored ("see attached," "as noted above").
- Using "I just" or "I wanted to" — both signal hedging.

## Output

Produce the email as plain text, ready to paste into Outlook or Gmail. Don't wrap it in markdown code fences. Don't add commentary before or after — just the email itself.
