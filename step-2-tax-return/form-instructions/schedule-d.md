# Schedule D Instructions — Capital Gains and Losses (AI-Optimized)
<!-- schema_version: 1.0 -->
<!-- last_updated: 2026-03-23 -->

> ⚠️ **IMPORTANT**: These instructions are AI-optimized summaries, not the official IRS instructions. You MUST cross-validate every threshold, rate, and limit against the [official Schedule D instructions](https://www.irs.gov/instructions/i1040sd) before producing a final tax return.

## When to Use This Form

Use Schedule D to report:
- Sales or exchanges of capital assets (stocks, bonds, mutual funds, real estate, crypto)
- Capital gain distributions from mutual funds or REITs (1099-DIV Box 2a)
- Nonbusiness bad debts
- Capital loss carryovers from prior years

**Prerequisite**: Complete **Form 8949** first — its totals flow into Schedule D.

## Line-by-Line Instructions

### Part I — Short-Term Capital Gains and Losses (held ≤ 1 year)

#### Line 1a: Short-Term Totals from 1099-B (Basis Reported — Box A)
- **Source**: Form 8949, Part I, Box A totals
- **Condition**: Transactions where basis WAS reported to the IRS and NO adjustments are needed
- **Note**: If no adjustments are needed, you can enter these directly on Line 1a without using Form 8949

#### Line 1b: Short-Term Totals from Form 8949, Box A
- **Source**: Form 8949, Part I, Box A summary line (when adjustments ARE needed)
- **Columns**: (d) proceeds, (e) cost basis, (g) adjustments, (h) gain or loss

#### Line 2: Short-Term Totals from Form 8949, Box B
- **Source**: Form 8949, Part I, Box B summary line
- **Condition**: Short-term transactions where basis was NOT reported to IRS

#### Line 3: Short-Term Totals from Form 8949, Box C
- **Source**: Form 8949, Part I, Box C summary line
- **Condition**: Short-term transactions not reported on Form 1099-B

#### Line 4: Short-Term Gain or Loss from Other Forms
- **Source**: Form 6252 (installment sales), Form 4684 (casualties), Form 6781 (section 1256 contracts), Form 8824 (like-kind exchanges)

#### Line 5: Net Short-Term Capital Gain or Loss from Partnerships, S Corporations, Estates, and Trusts
- **Source**: Schedule K-1 (Box 8 for partnership, Box 7 for S-corp)

#### Line 6: Short-Term Capital Loss Carryover
- **Source**: Prior year Schedule D, Capital Loss Carryover Worksheet
- **Enter**: As a negative number

#### Line 7: Net Short-Term Capital Gain or (Loss)
- **Calculation**: Sum of Lines 1a through 6

### Part II — Long-Term Capital Gains and Losses (held > 1 year)

#### Line 8a: Long-Term Totals from 1099-B (Basis Reported — Box D)
- **Source**: Form 8949, Part II, Box D totals
- **Condition**: Long-term transactions where basis WAS reported and NO adjustments needed

#### Line 8b: Long-Term Totals from Form 8949, Box D
- **Source**: Form 8949, Part II, Box D summary line (when adjustments ARE needed)

#### Line 9: Long-Term Totals from Form 8949, Box E
- **Source**: Form 8949, Part II, Box E summary line
- **Condition**: Long-term transactions where basis was NOT reported to IRS

#### Line 10: Long-Term Totals from Form 8949, Box F
- **Source**: Form 8949, Part II, Box F summary line
- **Condition**: Long-term transactions not reported on Form 1099-B

#### Line 11: Long-Term Gain or Loss from Other Forms
- **Source**: Same as Line 4 (long-term portion)

#### Line 12: Net Long-Term Capital Gain or Loss from Partnerships, S Corporations, Estates, and Trusts
- **Source**: Schedule K-1 (Box 9a for partnership, Box 8a for S-corp)

#### Line 13: Capital Gain Distributions
- **Source**: Sum of all 1099-DIV Box 2a amounts
- **Note**: Always long-term, even if you held the fund less than 1 year

#### Line 14: Long-Term Capital Loss Carryover
- **Source**: Prior year Schedule D, Capital Loss Carryover Worksheet
- **Enter**: As a negative number

#### Line 15: Net Long-Term Capital Gain or (Loss)
- **Calculation**: Sum of Lines 8a through 14

### Part III — Summary

#### Line 16: Combine Lines 7 and 15
- **Calculation**: Line 7 + Line 15
- **If positive**: You have a net capital gain
- **If negative**: You have a net capital loss (deduction limited — see below)

#### Lines 17–21: Tax Calculation Decision

```
Is Line 16 a gain?
├── Yes → Go to Line 21
│   └── Do you have 28% rate gain (Line 18) OR unrecaptured section 1250 gain (Line 19)?
│       ├── Yes → Complete the Schedule D Tax Worksheet (in instructions)
│       │   └── Enter result on Form 1040, Line 16
│       └── No → Do you have qualified dividends on Form 1040, Line 3a?
│           ├── Yes → Complete the Qualified Dividends and Capital Gain Tax Worksheet
│           │   └── Enter result on Form 1040, Line 16
│           └── No → Use the standard Tax Table or Tax Computation Worksheet
│               └── Enter result on Form 1040, Line 16
└── No (loss or zero) →
    └── Is the loss > $3,000 ($1,500 if MFS)?
        ├── Yes → Deduction limited to $3,000 ($1,500 MFS)
        │   └── Excess carries forward to next year
        └── No → Deduct the full loss amount
```

#### Line 21: Net Capital Gain or Loss
- **If gain**: Enter on Form 1040, Line 7
- **If loss**: Enter the **smaller** of: (a) the loss, or (b) $3,000 ($1,500 MFS) as a negative number on Form 1040, Line 7
- **Capital loss carryover**: If loss exceeds the $3,000 limit, complete the Capital Loss Carryover Worksheet to determine the amount carried to next year

## Capital Loss Carryover

If your total capital losses exceed $3,000 ($1,500 MFS):
1. The excess carries forward indefinitely
2. Short-term losses are used first, then long-term losses
3. Complete the **Capital Loss Carryover Worksheet** (in Schedule D instructions) to calculate next year's carryover
4. Keep this worksheet — you'll need it for next year's Schedule D Line 6 and Line 14

## Tax Rate Summary

| Type of Gain | Tax Rate | Notes |
|-------------|----------|-------|
| Short-term capital gain | Ordinary income rates | Same as wages |
| Long-term capital gain | 0%, 15%, or 20% | Based on taxable income — VERIFY brackets |
| Collectibles gain (28% rate) | Up to 28% | Art, antiques, coins, metals |
| Unrecaptured section 1250 gain | Up to 25% | Depreciation recapture on real estate |
| Qualified dividends | 0%, 15%, or 20% | Same rates as long-term capital gains |

> ⚠️ **VERIFY** capital gains tax rate brackets against the [current year IRS inflation adjustments](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments).

## Net Investment Income Tax (NIIT)

- An additional **3.8%** tax may apply to net investment income (including capital gains) if MAGI exceeds:
  - $250,000 (MFJ)
  - $200,000 (Single/HOH)
  - $125,000 (MFS)
- Reported on **Form 8960** → Schedule 2, Line 18
- **VERIFY** thresholds against [Form 8960 instructions](https://www.irs.gov/instructions/i8960)

## Key IRS Publication References

| Topic | Publication |
|-------|------------|
| Investment income and expenses | [Publication 550](https://www.irs.gov/publications/p550) |
| Capital gains and losses | [Publication 544](https://www.irs.gov/publications/p544) |
| Schedule D instructions | [Schedule D Instructions](https://www.irs.gov/instructions/i1040sd) |
| Form 8949 instructions | [Form 8949 Instructions](https://www.irs.gov/instructions/i8949) |
| Net Investment Income Tax | [Form 8960 Instructions](https://www.irs.gov/instructions/i8960) |
