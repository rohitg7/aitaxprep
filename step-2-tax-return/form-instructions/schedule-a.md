# Schedule A Instructions — Itemized Deductions (AI-Optimized)
<!-- schema_version: 1.0 -->
<!-- last_updated: 2026-03-23 -->

> ⚠️ **IMPORTANT**: These instructions are AI-optimized summaries, not the official IRS instructions. You MUST cross-validate every threshold, rate, and limit against the [official Schedule A instructions](https://www.irs.gov/instructions/i1040sa) and [current year IRS inflation adjustments](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments) before producing a final tax return.

## When to Use This Form

Use Schedule A to itemize deductions instead of taking the standard deduction. File Schedule A when:
- Itemized deductions exceed the standard deduction for your filing status
- You are married filing separately and your spouse itemizes (you MUST itemize)
- You are a nonresident alien (in some cases)

## Standard vs. Itemized Deduction Decision Tree

```
1. Look up standard deduction for filing status (VERIFY current year amounts):
   - Single: Check IRS
   - Married Filing Jointly: Check IRS
   - Married Filing Separately: Check IRS
   - Head of Household: Check IRS
   - Add additional amount if age 65+ or blind

2. Calculate total itemized deductions (Schedule A, Line 17)

3. Compare:
   ├── Itemized > Standard → File Schedule A (itemize)
   ├── Itemized ≤ Standard → Take standard deduction (do NOT file Schedule A)
   └── Exception: MFS and spouse itemizes → MUST file Schedule A regardless
```

## Line-by-Line Instructions

### Medical and Dental Expenses (Lines 1–4)

#### Line 1: Medical and Dental Expenses
- **Source**: Total medical/dental expenses paid during the tax year
- **Includes**: Doctor/dentist/hospital bills, prescription drugs, insulin, health insurance premiums (not pre-tax), eyeglasses, hearing aids, long-term care (limited), travel for medical care, Medicare Part B/D premiums
- **Does NOT include**: Cosmetic surgery, gym memberships, over-the-counter medicine (generally), health insurance premiums paid pre-tax through employer
- **IRS Verification**: [Publication 502](https://www.irs.gov/publications/p502)

#### Line 2: AGI
- **Source**: Form 1040, Line 11

#### Line 3: Multiply Line 2 by 7.5%
- **Calculation**: Line 2 × 0.075
- **Note**: VERIFY the 7.5% threshold against IRS — this percentage has changed in the past

#### Line 4: Deductible Medical Expenses
- **Calculation**: Line 1 - Line 3 (if result is ≤ 0, enter 0)
- **Example**: Medical expenses = 15000, AGI = 100000 → 15000 - (100000 × 0.075) = 15000 - 7500 = 7500.00 deductible

### Taxes You Paid (Lines 5a–5e)

#### Line 5a: State and Local Income Taxes (or General Sales Tax)
- **Choice**: Deduct EITHER state/local income taxes paid OR general sales taxes — not both
- **Income tax source**: W-2 Box 17 (state tax withheld) + state estimated tax payments + prior year state tax due payments
- **Sales tax**: Use IRS Sales Tax Deduction Calculator or optional sales tax tables
- **IRS Verification**: [Publication 600](https://www.irs.gov/publications/p600) (sales tax tables)

#### Line 5b: State and Local Real Estate Taxes
- **Source**: Property tax bills — total property tax actually **paid** during the year
- **Does NOT include**: Special assessments for improvements, trash fees, utility charges
- **Note**: Taxes on rental property go on Schedule E, not here

#### Line 5c: State and Local Personal Property Taxes
- **Source**: Vehicle registration fees (only the ad valorem / value-based portion), boat taxes
- **Note**: Only the portion based on the value of the property is deductible

#### Line 5d: Total (add Lines 5a through 5c)
- **Calculation**: Line 5a + Line 5b + Line 5c

#### Line 5e: SALT Cap — Enter the SMALLER of Line 5d or $10,000 ($5,000 if MFS)
- **Calculation**: min(Line 5d, 10000.00) — or min(Line 5d, 5000.00) if married filing separately
- **CRITICAL**: The $10,000 SALT cap applies to the COMBINED total of state/local income (or sales) tax + real estate tax + personal property tax
- **IRS Verification**: VERIFY the SALT cap is still in effect for the current tax year — check [Publication 5307](https://www.irs.gov/publications/p5307)

### Interest You Paid (Lines 8a–8e)

#### Line 8a: Home Mortgage Interest and Points (from Form 1098)
- **Source**: 1098 Box 1 (mortgage interest) + 1098 Box 6 (points)
- **Limit**: Interest on up to $750,000 of acquisition debt ($375,000 MFS); $1,000,000 limit for pre-12/16/2017 mortgages
- **IRS Verification**: [Publication 936](https://www.irs.gov/publications/p936)

#### Line 8b: Home Mortgage Interest Not Reported on Form 1098
- **Source**: Interest paid on a mortgage where the lender did not issue a 1098 (e.g., seller-financed mortgage)
- **Must provide**: Name, address, and SSN/TIN of the person/entity you paid interest to

#### Line 8c: Points Not Reported on Form 1098
- **Source**: Points paid on a mortgage not reported on Form 1098

#### Line 8d: Mortgage Insurance Premiums
- **Source**: 1098 Box 5
- **Note**: VERIFY current year availability — this deduction has expired and been extended multiple times
- **IRS Verification**: Check current year Form 1040 instructions

#### Line 8e: Total Interest (add Lines 8a through 8d)
- **Calculation**: Line 8a + Line 8b + Line 8c + Line 8d

### Gifts to Charity (Lines 11–14)

#### Line 11: Gifts by Cash or Check
- **Source**: Sum of all cash charitable donations
- **Substantiation**: Donations ≥ $250 require written acknowledgment from the charity
- **Limit**: Generally 60% of AGI for cash to public charities (VERIFY)
- **IRS Verification**: [Publication 526](https://www.irs.gov/publications/p526)

#### Line 12: Other Than by Cash or Check
- **Source**: Fair market value of noncash donations (clothing, household items, vehicles, stock, etc.)
- **Trigger**: If total noncash > $500 → **Form 8283** required
- **Trigger**: If single item > $5,000 → Qualified appraisal + Form 8283 Section B

#### Line 13: Carryover from Prior Year
- **Source**: Charitable contributions from prior years that exceeded AGI limits
- **Note**: Carryover is available for 5 years

#### Line 14: Total Gifts to Charity (add Lines 11 through 13)
- **Calculation**: Line 11 + Line 12 + Line 13

### Casualty and Theft Losses (Line 15)

#### Line 15: Casualty and Theft Losses
- **Source**: Form 4684
- **CRITICAL**: Only losses from a **federally declared disaster** are deductible (VERIFY current law)
- **IRS Verification**: [Publication 547](https://www.irs.gov/publications/p547) and [FEMA disaster declarations](https://www.fema.gov/disasters)

### Other Itemized Deductions (Line 16)

#### Line 16: Other Itemized Deductions
- **Includes**: Gambling losses (up to the amount of gambling winnings), casualty/theft losses of income-producing property, federal estate tax on income in respect of a decedent, unrecovered investment in annuity
- **Does NOT include**: Unreimbursed employee expenses (suspended through 2025 — VERIFY), tax preparation fees (suspended through 2025 — VERIFY)
- **IRS Verification**: Check current year Schedule A instructions for eligible deductions

### Total Itemized Deductions (Line 17)

#### Line 17: Total Itemized Deductions
- **Calculation**: Line 4 + Line 5e + Line 8e + Line 14 + Line 15 + Line 16
- **This amount** → Form 1040, Line 12 (if choosing to itemize)

## Key IRS Publication References

| Topic | Publication |
|-------|------------|
| Medical/dental expenses | [Publication 502](https://www.irs.gov/publications/p502) |
| Taxes you paid / SALT | [Publication 5307](https://www.irs.gov/publications/p5307) |
| Mortgage interest | [Publication 936](https://www.irs.gov/publications/p936) |
| Charitable contributions | [Publication 526](https://www.irs.gov/publications/p526) |
| Casualty and theft losses | [Publication 547](https://www.irs.gov/publications/p547) |
| General itemized deductions | [Schedule A Instructions](https://www.irs.gov/instructions/i1040sa) |
