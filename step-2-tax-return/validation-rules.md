# Validation Rules

These rules must be checked by the AI tool after generating `tax_return.md`. Include the results in the Validation Report section.

> ⚠️ These rules cover common checks. For comprehensive validation, consult the [official Form 1040 instructions](https://www.irs.gov/instructions/i1040).

## Cross-Form Consistency

These checks ensure values flow correctly between forms:

| Check | Rule |
|-------|------|
| W-2 wages | Form 1040 Line 1a = sum of all W-2 Box 1 values |
| W-2 withholding | Form 1040 Line 25a = sum of all W-2 Box 2 values |
| Taxable interest | Form 1040 Line 2b = sum of all 1099-INT Box 1 values |
| Ordinary dividends | Form 1040 Line 3b = sum of all 1099-DIV Box 1a values |
| Qualified dividends | Form 1040 Line 3a = sum of all 1099-DIV Box 1b values |
| Capital gains | Form 1040 Line 7 = Schedule D Line 21 (or Line 16) |
| Schedule D Part I | Schedule D Line 7 = Form 8949 Part I column (h) total |
| Schedule D Part II | Schedule D Line 15 = Form 8949 Part II column (h) total |
| Other income | Form 1040 Line 8 = Schedule 1 Line 10 |
| Adjustments | Form 1040 Line 10 = Schedule 1 Line 26 |
| SE tax | Schedule 2 Part II includes Schedule SE Line 12 |
| 1099 withholding | Form 1040 Line 25b = sum of all 1099 forms' federal withholding |

## Mathematical Checks

| Line | Formula |
|------|---------|
| 1040 Line 9 | = sum of Lines 1z through 8 |
| 1040 Line 11 | = Line 9 - Line 10 |
| 1040 Line 14 | = Line 12 + Line 13 |
| 1040 Line 15 | = max(0, Line 11 - Line 14) |
| 1040 Line 18 | = Line 16 + Line 17 |
| 1040 Line 21 | = Line 19 + Line 20 |
| 1040 Line 22 | = max(0, Line 18 - Line 21) |
| 1040 Line 24 | = Line 22 + Line 23 |
| 1040 Line 25d | = Line 25a + Line 25b + Line 25c |
| 1040 Line 33 | = sum of Lines 25d through 32 |
| 1040 Line 34 | = max(0, Line 33 - Line 24) |
| 1040 Line 37 | = max(0, Line 24 - Line 33) |
| Schedule D Line 16 | = Line 7 + Line 15 |

## Business Logic Checks

| Check | Rule |
|-------|------|
| Qualified dividends | Line 3a must be ≤ Line 3b (qualified is subset of ordinary) |
| Capital loss limit | If Line 7 is negative, must be ≥ -3000.00 (or -1500.00 if MFS) |
| Standard deduction | If itemizing, verify Schedule A total > standard deduction |
| Taxable income floor | Line 15 cannot be negative (minimum 0.00) |
| Tax amount | Line 16 should be reasonable for the taxable income and filing status |
| Refund XOR owe | Either Line 34 > 0 OR Line 37 > 0 (not both) |
| SE tax trigger | If Schedule C net profit > 400, Schedule SE must be present |
| Schedule B trigger | If interest > 1500 OR dividends > 1500, Schedule B must be present |
| SSN format | All SSNs masked as `***-**-XXXX` |

## Common Errors to Catch

| Error | Description |
|-------|-------------|
| Missing SE deduction | Forgetting the 50% self-employment tax deduction on Schedule 1 Line 15 |
| Wrong capital loss limit | Not capping capital loss deduction at $3,000 |
| State refund omission | Not reporting state/local tax refund (1099-G) as income if prior year itemized |
| Double counting | Including the same income on multiple lines |
| Missing withholding | Not including all W-2 and 1099 withholding in payments |
| Wrong filing status | Using head_of_household without qualifying dependent |
| MFS itemization | If MFS, must itemize if spouse itemizes |
| Wash sale adjustment | Not adjusting cost basis for wash sale losses disallowed on 1099-B |

## IRS-Verified Checks

After completing the return, verify these values against the IRS:

| What to Verify | IRS Source |
|----------------|-----------|
| Standard deduction for filing status | Current year Revenue Procedure |
| Tax bracket thresholds | Current year Revenue Procedure |
| Capital loss limit ($3,000 / $1,500) | Publication 550 |
| SE tax rate (15.3% / 2.9%) | Publication 334 |
| SALT deduction cap ($10,000) | Publication 5307 |
| Child tax credit amount | IRS.gov/credits-deductions |
| EITC income limits | Publication 596 |
