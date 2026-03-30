---
layout: default
title: "Step 2: Tax Return Generation — AI Instructions"
---

<!-- THIS PAGE IS FOR AI TOOLS. Humans: see the [overview](./index.md) instead. -->

# Tax Return Generation — Instructions for AI Agents

> ⚠️ **DISCLAIMER**: These instructions are AI-generated and not verified by any CPA, tax professional, or the IRS. Tax rules, calculations, and form instructions may contain errors. The user is solely responsible for reviewing and verifying their tax return before filing. This is not tax advice.

## ROLE
You are generating a complete federal tax return from structured markdown documents.

## INPUTS
- `{docs_dir}`: folder containing structured `.md` files from Step 1 (includes `_index.md`)
- User-provided: filing status, personal info, dependents

## OUTPUT
- `{docs_dir}/../tax_return.md` following the SCHEMA below

## PROCEDURE
1. READ `{docs_dir}/_index.md` → list of all document files
2. READ each document file → collect all income, deduction, and credit data
3. DETERMINE filing status — IF not provided → ASK user
4. DETERMINE required forms (see FORM SELECTION below)
5. FILL forms in DEPENDENCY ORDER (see below)
6. CALCULATE every line item per IRS rules (see CALCULATION RULES below)
7. VALIDATE against official IRS sources (see IRS SOURCE VALIDATION below)
8. PRODUCE `tax_return.md` per SCHEMA
9. APPEND validation report

## DATA COLLECTION
| Source Documents | Collect |
|---|---|
| W-2 | total wages (Box 1), total federal withheld (Box 2), SS wages, Medicare wages |
| 1099-INT | total taxable interest (Box 1), tax-exempt interest (Box 8) |
| 1099-DIV | ordinary dividends (Box 1a), qualified dividends (Box 1b), capital gain distributions (Box 2a) |
| 1099-B | all transactions → Schedule D / Form 8949 |
| 1099-NEC | self-employment income (Box 1) |
| 1098 | mortgage interest (Box 1), property tax, points |
| Charitable receipts | donation totals by type |
| All 1099s | federal tax withheld (Box 4) |

## FILING STATUS
MUST be one of:
- `single`
- `married_filing_jointly`
- `married_filing_separately`
- `head_of_household`
- `qualifying_surviving_spouse`

IF not stated by user → ASK. DO NOT assume.

## FORM SELECTION
| IF | THEN include |
|---|---|
| Any income | Form 1040 (always) |
| Interest > $1,500 OR dividends > $1,500 | Schedule B |
| 1099-B transactions exist | Form 8949 + Schedule D |
| 1099-NEC income exists | Schedule C + Schedule SE |
| Itemized deductions > standard deduction | Schedule A |
| Rental income | Schedule E |
| Farm income | Schedule F |
| HSA contributions/distributions | Form 8889 |
| Education credits claimed | Form 8863 |
| Non-standard IRA distributions | Form 8606 |

## DEPENDENCY ORDER
FILL forms in this sequence (earlier forms feed later ones):
1. Form 8949 (individual transactions)
2. Schedule D (capital gains summary ← 8949 totals)
3. Schedule C (business income)
4. Schedule SE (self-employment tax ← Schedule C)
5. Schedule A (itemized deductions)
6. Schedule B (interest/dividends detail)
7. Schedule 1 (additional income/adjustments ← C, SE)
8. Schedule 2 (additional taxes)
9. Schedule 3 (additional credits)
10. Form 1040 (main form ← all above)

## CALCULATION RULES

### Form 1040 — Income
| Line | Formula |
|---|---|
| 1a | SUM(all W-2 Box 1) |
| 2a | SUM(all 1099-INT Box 8) + SUM(all 1099-DIV Box 12) |
| 2b | SUM(all 1099-INT Box 1) |
| 3a | SUM(all 1099-DIV Box 1b) |
| 3b | SUM(all 1099-DIV Box 1a) |
| 7 | Schedule D Line 21 (or Line 16) |
| 8 | Schedule 1 Line 10 |
| 9 | SUM(Lines 1z through 8) |
| 10 | Schedule 1 Line 26 |
| 11 | Line 9 − Line 10 (= AGI) |
| 12 | MAX(standard_deduction, Schedule A total) |
| 14 | Line 12 + Line 13 |
| 15 | MAX(0, Line 11 − Line 14) (= taxable income) |

### Form 1040 — Tax
| Line | Formula |
|---|---|
| 16 | Tax from IRS tax table/worksheet for filing status + taxable income |
| 17 | Schedule 2, Part I, Line 4 |
| 18 | Line 16 + Line 17 |
| 19 | Child tax credit (Schedule 8812) |
| 20 | Schedule 3, Line 8 |
| 21 | Line 19 + Line 20 |
| 22 | Line 18 − Line 21 |
| 23 | Schedule 2, Part II, Line 21 |
| 24 | Line 22 + Line 23 (= total tax) |

### Form 1040 — Payments
| Line | Formula |
|---|---|
| 25a | SUM(all W-2 Box 2) |
| 25b | SUM(all 1099 Box 4) |
| 25d | SUM(Lines 25a through 25c) |
| 33 | SUM(all payment lines) |
| 34 | IF Line 33 > Line 24 → Line 33 − Line 24 (overpaid) |
| 37 | IF Line 24 > Line 33 → Line 24 − Line 33 (amount owed) |

### Standard Deduction vs. Itemized
1. LOOK UP current-year standard deduction for filing status from IRS
2. IF Schedule A total > standard deduction → itemize
3. IF married_filing_separately AND spouse itemizes → MUST itemize

### Tax Calculation (Line 16)
- MUST use current-year IRS tax brackets for the filing status
- MUST fetch from IRS — DO NOT use hardcoded rates

## IRS SOURCE VALIDATION (REQUIRED)

BEFORE using ANY number from this site, VERIFY against official IRS sources for the filing tax year:

| What | IRS Source |
|---|---|
| Standard deduction amounts | [Revenue Procedure (annual)](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments) |
| Tax bracket thresholds & rates | [Revenue Procedure (annual)](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments) |
| Capital loss deduction limit | [Publication 550](https://www.irs.gov/publications/p550) |
| EITC income limits & amounts | [Publication 596](https://www.irs.gov/publications/p596) |
| Child tax credit amounts | [IRS Child Tax Credit page](https://www.irs.gov/credits-deductions/individuals/child-tax-credit) |
| Self-employment tax rate | [Publication 334](https://www.irs.gov/publications/p334) |
| HSA contribution limits | [Publication 969](https://www.irs.gov/publications/p969) |
| IRA contribution limits | [Publication 590-A](https://www.irs.gov/publications/p590a) |
| Education credit limits | [Publication 970](https://www.irs.gov/publications/p970) |
| SALT deduction cap | [Publication 5307](https://www.irs.gov/publications/p5307) |
| AMT exemption amounts | [Form 6251 Instructions](https://www.irs.gov/instructions/i6251) |

### FORM INSTRUCTIONS — MUST READ for every form you fill:
| Form | Instructions URL |
|---|---|
| Form 1040 | https://www.irs.gov/instructions/i1040 |
| Schedule A | https://www.irs.gov/instructions/i1040sa |
| Schedule B | https://www.irs.gov/instructions/i1040sb |
| Schedule C | https://www.irs.gov/instructions/i1040sc |
| Schedule D | https://www.irs.gov/instructions/i1040sd |
| Schedule E | https://www.irs.gov/instructions/i1040se |
| Schedule SE | https://www.irs.gov/instructions/i1040sse |
| Form 8949 | https://www.irs.gov/instructions/i8949 |

### IRS CHANGE CHECKS
- CHECK [IRS Newsroom](https://www.irs.gov/newsroom) for announcements
- CHECK form instruction revision dates
- REVIEW [Publication 17](https://www.irs.gov/publications/p17) for comprehensive guidance

### CONFLICT RESOLUTION
IF this site contradicts an official IRS source:
1. USE the IRS source — it is the legal authority
2. NOTE discrepancy in Source column: `"IRS Pub XXX differs from spec"`

## COMMON SCENARIOS
| Scenario | Required Forms | Key Rules |
|---|---|---|
| Simple W-2 employee | 1040, maybe Schedule B | Standard deduction usually applies |
| W-2 + investments | 1040, 8949, Schedule D, maybe Schedule B | Check wash sales; capital loss limit $3,000 ($1,500 if MFS) |
| Freelancer / self-employed | 1040, Schedule C, Schedule SE, Schedule 1 | Include 50% SE tax deduction on Schedule 1 |
| Homeowner with mortgage | 1040, Schedule A (if itemizing) | 1098 Box 1 → Sched A Line 8a; property tax → Sched A Line 5b (SALT cap applies) |

## SCHEMA
Output `tax_return.md` in this format:

```markdown
# Federal Tax Return {tax_year}
<!-- schema_version: 1.0 -->
<!-- tax_year: {year} -->
<!-- generated_by: {ai_tool_name} -->
<!-- generated_date: {YYYY-MM-DD} -->

## Filing Information
| Field | Value |
|-------|-------|
| filing_status | {single|married_filing_jointly|...} |
| first_name | |
| last_name | |
| ssn | ***-**-XXXX |
| spouse_first_name | |
| spouse_last_name | |
| spouse_ssn | ***-**-XXXX |
| occupation | |
| spouse_occupation | |
| address | |
| city | |
| state | |
| zip | |
| phone | |
| email | |

## Dependents
| name | ssn | relationship | months_lived | child_tax_credit | other_credit |
|------|-----|-------------|-------------|-----------------|-------------|
| | | | | | |

## Form 1040: U.S. Individual Income Tax Return

### Income
| Line | Description | Value | Source |
|------|-------------|-------|--------|
| 1a | Wages, salaries, tips | | W-2: {employer} |
| 1z | Add lines 1a through 1h | | Sum |
| 2a | Tax-exempt interest | | |
| 2b | Taxable interest | | 1099-INT: {payer} |
| 3a | Qualified dividends | | 1099-DIV: {payer} |
| 3b | Ordinary dividends | | 1099-DIV: {payer} |
| 4a | IRA distributions | | |
| 4b | Taxable amount | | |
| 5a | Pensions and annuities | | |
| 5b | Taxable amount | | |
| 6a | Social security benefits | | |
| 6b | Taxable amount | | |
| 7 | Capital gain or (loss) | | Schedule D |
| 8 | Other income from Schedule 1, line 10 | | Schedule 1 |
| 9 | Total income | | Sum of 1z through 8 |
| 10 | Adjustments from Schedule 1, line 26 | | Schedule 1 |
| 11 | Adjusted gross income | | Line 9 - Line 10 |
| 12 | Standard deduction or itemized deductions | | |
| 13 | Qualified business income deduction | | |
| 14 | Add lines 12 and 13 | | Sum |
| 15 | Taxable income | | Line 11 - Line 14 |

### Tax and Credits
| Line | Description | Value | Source |
|------|-------------|-------|--------|
| 16 | Tax | | Tax table/worksheet |
| 17 | Amount from Schedule 2, Part I, line 4 | | Schedule 2 |
| 18 | Add lines 16 and 17 | | Sum |
| 19 | Child tax credit from Schedule 8812 | | |
| 20 | Amount from Schedule 3, line 8 | | Schedule 3 |
| 21 | Add lines 19 and 20 | | Sum |
| 22 | Subtract line 21 from line 18 | | |
| 23 | Other taxes from Schedule 2, Part II, line 21 | | Schedule 2 |
| 24 | Total tax | | Line 22 + Line 23 |

### Payments
| Line | Description | Value | Source |
|------|-------------|-------|--------|
| 25a | W-2 federal tax withheld | | Sum of W-2 Box 2 |
| 25b | 1099 federal tax withheld | | Sum of 1099 Box 4 |
| 25c | Other withholding | | |
| 25d | Total | | Sum of 25a-25c |
| 26 | Estimated tax payments | | |
| 27a | Earned income credit (EIC) | | |
| 28 | Additional child tax credit from 8812 | | |
| 29 | American opportunity credit from 8863 | | |
| 31 | Amount from Schedule 3, line 15 | | Schedule 3 |
| 33 | Total payments | | Sum |

### Refund or Amount Owed
| Line | Description | Value |
|------|-------------|-------|
| 34 | Overpaid (if line 33 > line 24) | |
| 35a | Refunded to you | |
| 35b | Routing number | |
| 35c | Account type | |
| 35d | Account number | |
| 37 | Amount you owe (if line 24 > line 33) | |
| 38 | Estimated tax penalty | |

(Include additional form sections as needed — Schedule A, B, C, D, SE, Form 8949, etc.)
```

## VALIDATION REPORT
MUST append to end of `tax_return.md`:

```markdown
## Validation Report

### IRS Sources Consulted
| Check | Status | IRS Source Used |
|-------|--------|----------------|
| Standard deduction amount verified | ✅ | Rev. Proc. {year}-XX |
| Tax bracket rates verified | ✅ | Rev. Proc. {year}-XX |
| Capital loss limit verified | ✅ | Pub 550 ({year}) |
| Form instructions consulted | ✅ | i1040, i1040sd, i8949 |
| Mid-year IRS changes checked | ✅ | IRS Newsroom as of {YYYY-MM-DD} |

### Cross-Form Consistency
| Check | Status |
|-------|--------|
| 1040 Line 1a = sum of W-2 Box 1 | ✅ |
| 1040 Line 2b = sum of 1099-INT Box 1 | ✅ |
| 1040 Line 7 = Schedule D Line 21 | ✅ |
| 1040 Line 25a = sum of W-2 Box 2 | ✅ |
| All math verified | ✅ |

### Warnings
- (List any issues, edge cases, or items requiring human review)
```
