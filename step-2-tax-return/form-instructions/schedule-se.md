# Schedule SE Instructions — Self-Employment Tax (AI-Optimized)
<!-- schema_version: 1.0 -->
<!-- last_updated: 2026-03-23 -->

> ⚠️ **IMPORTANT**: These instructions are AI-optimized summaries, not the official IRS instructions. You MUST cross-validate every threshold, rate, and limit against the [official Schedule SE instructions](https://www.irs.gov/instructions/i1040sse) and [current year IRS inflation adjustments](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments) before producing a final tax return.

## When to Use This Form

Use Schedule SE to calculate self-employment tax if:
- Net self-employment earnings are **$400 or more**
- You had church employee income of $108.28 or more (VERIFY threshold)

Self-employment tax consists of:
- **Social Security tax**: 12.4% (combined employer + employee share) — VERIFY rate
- **Medicare tax**: 2.9% (combined employer + employee share) — VERIFY rate
- **Total SE tax rate**: 15.3% on net earnings up to the Social Security wage base — VERIFY
- **Medicare-only rate**: 2.9% on earnings above the Social Security wage base (no cap)
- **Additional Medicare tax**: 0.9% on earnings above $200,000 ($250,000 MFJ) — VERIFY thresholds

> ⚠️ **VERIFY** the SE tax rate, Social Security wage base, and Additional Medicare Tax thresholds against [IRS Publication 334](https://www.irs.gov/publications/p334) and the [current year inflation adjustments](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments).

## Short Schedule SE vs. Long Schedule SE

```
Can you use the Short Schedule SE (Section A)?
├── Use Short SE if ALL of the following are true:
│   ├── Net self-employment earnings are $400 or more
│   ├── You are NOT a minister or member of a religious order
│   ├── You are NOT filing Form 4361 (exemption from SE tax)
│   ├── You did NOT have church employee income ≥ $108.28
│   ├── You did NOT have wages subject to Social Security tax from
│   │   an employer AND net SE earnings AND total exceeds the
│   │   Social Security wage base
│   └── You are NOT using an optional method to figure SE tax
├── If ALL true → Use Short Schedule SE (Section A)
└── If ANY false → Use Long Schedule SE (Section B)
```

Most filers with straightforward self-employment income (1099-NEC / Schedule C) use the **Short Schedule SE**.

## Short Schedule SE (Section A) — Line-by-Line

#### Line 1a: Net Farm Profit or (Loss)
- **Source**: Schedule F, Line 34 (or farm partnership K-1)
- **Most filers**: Enter 0

#### Line 1b: Net Farm Profit or (Loss) — Optional Method
- **Source**: Only if using the nonfarm optional method
- **Most filers**: Skip

#### Line 2: Net Profit or (Loss) from Nonfarm Business
- **Source**: Schedule C, Line 31 + any partnership K-1 Box 14 (self-employment earnings)
- **Note**: If you have multiple Schedule Cs, combine all net profits/losses

#### Line 3: Combine Lines 1a, 1b, and 2
- **Calculation**: Line 1a + Line 1b + Line 2

#### Line 4a: If Line 3 is more than zero, multiply by 92.35%
- **Calculation**: Line 3 × 0.9235
- **Purpose**: This is the "employer equivalent" adjustment — a self-employed person deducts the equivalent of the employer's share before calculating SE tax
- **VERIFY**: The 92.35% factor against current IRS instructions

#### Line 4b: If using optional method
- **Most filers**: Skip

#### Line 4c: Combine Lines 4a and 4b
- **Calculation**: Line 4a + Line 4b
- **This is**: Net self-employment earnings

#### Line 5: Self-Employment Tax
- **Calculation**: Apply the SE tax rate schedule:
  1. If Line 4c ≤ Social Security wage base (VERIFY amount):
     - SE tax = Line 4c × 15.3%
  2. If Line 4c > Social Security wage base:
     - SE tax = (wage base × 12.4%) + (Line 4c × 2.9%)
- **VERIFY**: The Social Security wage base changes annually

#### Line 6: Deductible Part of Self-Employment Tax
- **Calculation**: Line 5 × 50%
- **Purpose**: You can deduct half of your SE tax as an income adjustment
- **Flows to**: Schedule 1, Line 15

## Where Schedule SE Results Flow

| Schedule SE Line | Flows To |
|-----------------|----------|
| Line 5 (SE tax) | Schedule 2, Part II, Line 4 → Form 1040, Line 23 (other taxes) |
| Line 6 (50% of SE tax) | Schedule 1, Line 15 (deductible part of SE tax) → reduces AGI |

## Calculation Example

```
Schedule C net profit:           $80,000.00
× 92.35%:                        $73,880.00 (net SE earnings)
× 15.3% (SE tax rate):           $11,303.64 (total SE tax)
× 50% (deductible portion):       $5,651.82 (deduction on Schedule 1)

Net effect on taxes:
  Income tax on $80,000 (at marginal rate)
+ SE tax of $11,303.64
- Income tax savings from $5,651.82 deduction
```

## Additional Medicare Tax

If net self-employment earnings (combined with wages) exceed:
- $200,000 (Single, HOH)
- $250,000 (MFJ)
- $125,000 (MFS)

An additional **0.9% Medicare tax** applies to the excess. This is calculated on **Form 8959** (Additional Medicare Tax).

```
Total Medicare wages (W-2 Box 5) + SE earnings > threshold?
├── Yes → File Form 8959
│   └── Additional 0.9% tax on amount exceeding threshold
│   └── Report on Schedule 2, Line 23 (or as directed)
└── No → No additional Medicare tax
```

> ⚠️ **VERIFY** these thresholds against [Form 8959 instructions](https://www.irs.gov/instructions/i8959).

## Triggers

- Schedule C net profit > 400.00 → **Schedule SE** required
- Schedule SE Line 5 > 0 → **Schedule 2, Part II** (additional taxes)
- Schedule SE Line 6 > 0 → **Schedule 1, Line 15** (SE tax deduction)
- Combined wages + SE earnings above Medicare threshold → **Form 8959** (Additional Medicare Tax)

## Important Notes

- **SE tax is in ADDITION to income tax** — self-employed individuals pay both
- The 50% deduction reduces **income tax** but does NOT reduce SE tax itself
- If you also have W-2 wages subject to Social Security, those wages reduce the amount of SE earnings subject to the 12.4% Social Security portion
- Church ministers may opt out of SE tax with Form 4361 (but this is irrevocable)
- **Estimated tax payments**: Self-employed individuals generally must make quarterly estimated tax payments (Form 1040-ES) to avoid underpayment penalties

## Key IRS Publication References

| Topic | Publication |
|-------|------------|
| Self-employment tax | [Publication 334](https://www.irs.gov/publications/p334) |
| SE tax general guidance | [Publication 533](https://www.irs.gov/publications/p533) |
| Schedule SE instructions | [Schedule SE Instructions](https://www.irs.gov/instructions/i1040sse) |
| Estimated tax payments | [Publication 505](https://www.irs.gov/publications/p505) |
| Additional Medicare Tax | [Form 8959 Instructions](https://www.irs.gov/instructions/i8959) |
