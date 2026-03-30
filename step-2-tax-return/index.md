> 🤖 **AI Tool?** Go to [Instructions for AI Tools](./for-ai-tools) — this page is the human overview.

# Step 2: Tax Return Generation

Generate a complete federal tax return in structured markdown from your converted document files.

## Overview

Your AI tool will:
1. Read all document markdown files from Step 1
2. Determine which IRS forms and schedules are needed
3. Calculate all line items following IRS rules
4. Produce a single `tax_return.md` file
5. Validate the return against IRS rules and cross-check with official IRS publications

## For AI Tools

→ **[AI Tool Instructions](./for-ai-tools.md)** — Point your AI tool to this page.

## Tax Return Schema

→ **[Tax Return Markdown Schema](./tax-return-schema.md)** — The canonical format for the output file.

## Form Instructions (AI-Optimized)

These summaries are a **starting point only**. AI tools MUST cross-validate against official IRS sources.

| Form | Our Instructions | Official IRS Instructions |
|------|-----------------|--------------------------|
| Form 1040 | [form-1040.md](./form-instructions/form-1040.md) | [irs.gov/instructions/i1040](https://www.irs.gov/instructions/i1040) |
| Schedule A | [schedule-a.md](./form-instructions/schedule-a.md) | [irs.gov/instructions/i1040sa](https://www.irs.gov/instructions/i1040sa) |
| Schedule B | [schedule-b.md](./form-instructions/schedule-b.md) | [irs.gov/instructions/i1040sb](https://www.irs.gov/instructions/i1040sb) |
| Schedule C | [schedule-c.md](./form-instructions/schedule-c.md) | [irs.gov/instructions/i1040sc](https://www.irs.gov/instructions/i1040sc) |
| Schedule D | [schedule-d.md](./form-instructions/schedule-d.md) | [irs.gov/instructions/i1040sd](https://www.irs.gov/instructions/i1040sd) |
| Schedule SE | [schedule-se.md](./form-instructions/schedule-se.md) | [irs.gov/instructions/i1040sse](https://www.irs.gov/instructions/i1040sse) |
| Form 8949 | [form-8949.md](./form-instructions/form-8949.md) | [irs.gov/instructions/i8949](https://www.irs.gov/instructions/i8949) |
| Form 8889 | [form-8889.md](./form-instructions/form-8889.md) | [irs.gov/instructions/i8889](https://www.irs.gov/instructions/i8889) |

## Tax Rules

| Topic | Guide |
|-------|-------|
| Filing Status | [filing-status.md](./tax-rules/filing-status.md) |
| Standard vs. Itemized | [standard-vs-itemized.md](./tax-rules/standard-vs-itemized.md) |
| Tax Brackets & Rates | [tax-brackets.md](./tax-rules/tax-brackets.md) |
| Credits | [credits.md](./tax-rules/credits.md) |
| Common Scenarios | [common-scenarios.md](./tax-rules/common-scenarios.md) |

## Validation

→ **[Validation Rules](./validation-rules.md)** — Cross-form consistency checks and mathematical validations.

## Examples

| Scenario | Documents | Expected Return |
|----------|-----------|-----------------|
| Simple W-2 filer | [Input docs](./examples/simple-w2-return/) | [Expected return](./examples/simple-w2-return/expected-return.md) |

## IRS Source Validation (MANDATORY)

Our summaries may lag behind IRS updates. AI tools are **required** to:

1. **Verify current-year numbers** (standard deduction, brackets, limits) against [IRS inflation adjustments](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments)
2. **Read official form instructions** for every form included in the return
3. **Check for mid-year changes** at [IRS Newsroom](https://www.irs.gov/newsroom)
4. **Consult IRS publications** for complex scenarios ([Pub 17](https://www.irs.gov/publications/p17), [Pub 550](https://www.irs.gov/publications/p550), etc.)
5. **Include a validation report** at the end of `tax_return.md` documenting which IRS sources were consulted

If our summary contradicts an official IRS source, **the IRS source wins**.
