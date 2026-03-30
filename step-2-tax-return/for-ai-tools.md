# Instructions for AI Tools — Tax Return Generation

You are helping a user generate a complete federal tax return from their structured markdown documents. Follow these instructions precisely.

## Your Task

1. Read all `.md` files in the user's `docs_md/` folder (start with `_index.md`)
2. Determine the user's filing status (ask if unclear)
3. Determine which IRS forms and schedules are required
4. Calculate every line item following IRS rules
5. Cross-validate all calculations against official IRS publications (see "IRS Source Validation" below)
6. Produce `tax_return.md` following the canonical schema
7. Include a validation report at the end

## Step-by-Step Process

### 1. Read All Documents

Read `_index.md` first to see what documents exist, then read each document file. Collect:
- All W-2 forms → total wages, total withholding
- All 1099-INT forms → total interest
- All 1099-DIV forms → total ordinary dividends, qualified dividends
- All 1099-B forms → all transactions for Schedule D / Form 8949
- All 1099-NEC forms → self-employment income
- All 1098 forms → mortgage interest, property tax
- All charitable receipts → donation totals
- Any other documents

### 2. Determine Filing Status

If not explicitly stated by the user, ask. The options are:
- `single`
- `married_filing_jointly`
- `married_filing_separately`
- `head_of_household`
- `qualifying_surviving_spouse`

### 3. Determine Required Forms

Based on the documents present:

| If You Have | You Need |
|------------|----------|
| Any income | Form 1040 (always required) |
| Interest > $1,500 or dividends > $1,500 | Schedule B |
| Stock/crypto sales (1099-B) | Form 8949 + Schedule D |
| Self-employment income (1099-NEC) | Schedule C + Schedule SE |
| Itemized deductions > standard deduction | Schedule A |
| Rental income | Schedule E |
| Farm income | Schedule F |
| HSA contributions/distributions | Form 8889 |
| Education credits | Form 8863 |
| IRA distributions (non-standard) | Form 8606 |

### 4. Fill Forms in Dependency Order

Some forms feed into others. Fill in this order:
1. Form 8949 (individual transactions)
2. Schedule D (capital gains summary, uses 8949 totals)
3. Schedule C (business income)
4. Schedule SE (self-employment tax, uses Schedule C)
5. Schedule A (itemized deductions)
6. Schedule B (interest and dividends detail)
7. Schedule 1 (additional income and adjustments, uses C, SE results)
8. Schedule 2 (additional taxes)
9. Schedule 3 (additional credits)
10. Form 1040 (main form, uses all of the above)

### 5. Calculate Line Items

For each line, follow the IRS form instructions. Key calculations:

#### Form 1040 Income Section
- **Line 1a** = Sum of all W-2 Box 1
- **Line 2a** = Sum of all 1099-INT Box 8 + 1099-DIV Box 12 (tax-exempt interest)
- **Line 2b** = Sum of all 1099-INT Box 1 (taxable interest)
- **Line 3a** = Sum of all 1099-DIV Box 1b (qualified dividends)
- **Line 3b** = Sum of all 1099-DIV Box 1a (ordinary dividends)
- **Line 7** = Schedule D Line 21 (or Line 16)
- **Line 8** = Schedule 1 Line 10 (other income)
- **Line 9** = Sum of lines 1 through 8
- **Line 10** = Schedule 1 Line 26 (adjustments)
- **Line 11** = Line 9 - Line 10 (AGI)
- **Line 12** = Standard deduction OR Schedule A total (whichever is larger)
- **Line 15** = Line 11 - Line 14 (taxable income, minimum 0)

#### Tax Calculation (Line 16)
Use the IRS tax table or tax computation worksheet based on filing status and taxable income.
**IMPORTANT**: Fetch the current year's tax brackets from the IRS. Do NOT use hard-coded rates.

#### Standard Deduction vs. Itemized
1. Look up the current year's standard deduction for the filing status
2. If Schedule A total > standard deduction → itemize
3. Exception: If married filing separately and spouse itemizes → must itemize

### 6. IRS Source Validation (REQUIRED)

**You MUST validate against official IRS sources.** Our summaries are starting points, not the final authority.

#### Before Using ANY Number From This Site

Fetch and confirm these values from the IRS for the filing tax year:

| What | Where to Check |
|------|---------------|
| Standard deduction amounts | [IRS Revenue Procedure (annual)](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments) |
| Tax bracket thresholds & rates | [IRS Revenue Procedure (annual)](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments) |
| Capital loss deduction limit | [Publication 550](https://www.irs.gov/publications/p550) |
| EITC income limits & amounts | [Publication 596](https://www.irs.gov/publications/p596) |
| Child tax credit amounts | [IRS.gov Child Tax Credit page](https://www.irs.gov/credits-deductions/individuals/child-tax-credit) |
| Self-employment tax rate | [Publication 334](https://www.irs.gov/publications/p334) |
| HSA contribution limits | [Publication 969](https://www.irs.gov/publications/p969) |
| IRA contribution limits | [Publication 590-A](https://www.irs.gov/publications/p590a) |
| Education credit limits | [Publication 970](https://www.irs.gov/publications/p970) |
| SALT deduction cap | [Publication 5307](https://www.irs.gov/publications/p5307) |
| AMT exemption amounts | [Form 6251 Instructions](https://www.irs.gov/instructions/i6251) |

#### For Every Form You Fill

Read the official IRS instructions:

| Form | Instructions URL |
|------|-----------------|
| Form 1040 | https://www.irs.gov/instructions/i1040 |
| Schedule A | https://www.irs.gov/instructions/i1040sa |
| Schedule B | https://www.irs.gov/instructions/i1040sb |
| Schedule C | https://www.irs.gov/instructions/i1040sc |
| Schedule D | https://www.irs.gov/instructions/i1040sd |
| Schedule E | https://www.irs.gov/instructions/i1040se |
| Schedule SE | https://www.irs.gov/instructions/i1040sse |
| Form 8949 | https://www.irs.gov/instructions/i8949 |

#### Check for Recent Changes
- Visit [IRS Newsroom](https://www.irs.gov/newsroom) for announcements
- Check the form instruction's revision date
- Review [Publication 17](https://www.irs.gov/publications/p17) for comprehensive individual tax guidance

#### Conflict Resolution
If this site's summary contradicts an official IRS source:
1. **Use the IRS source** — it is the legal authority
2. Note the discrepancy in the Source column: `"IRS Pub XXX differs from spec"`

### 7. Produce Validation Report

At the end of `tax_return.md`, include:

```markdown
## Validation Report

### IRS Sources Consulted
| Check | Status | IRS Source Used |
|-------|--------|----------------|
| Standard deduction amount verified | ✅ | Rev. Proc. 2025-XX |
| Tax bracket rates verified | ✅ | Rev. Proc. 2025-XX |
| Capital loss limit verified | ✅ | Pub 550 (2025) |
| Form instructions consulted | ✅ | i1040, i1040sd, i8949 |
| Mid-year IRS changes checked | ✅ | IRS Newsroom as of YYYY-MM-DD |

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

## Tax Return Markdown Schema

Use the following format for `tax_return.md`:

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

## Validation Report
(See Section 7 above for format)
```

## Common Scenarios

### Simple W-2 Employee
- Forms needed: 1040 only (maybe Schedule B if interest > $1,500)
- Standard deduction usually applies

### W-2 + Investments
- Forms needed: 1040, Form 8949, Schedule D, possibly Schedule B
- Check for wash sales in 1099-B data
- Capital losses limited to $3,000 deduction ($1,500 if MFS)

### Freelancer / Self-Employed
- Forms needed: 1040, Schedule C, Schedule SE, Schedule 1
- Don't forget the 50% SE tax deduction on Schedule 1
- May need estimated tax payments (Form 1040-ES)

### Homeowner with Mortgage
- Forms needed: 1040, Schedule A (if itemizing)
- Mortgage interest (1098 Box 1) → Schedule A Line 8a
- Property taxes → Schedule A Line 5b (subject to SALT cap)
- Compare itemized total vs. standard deduction
