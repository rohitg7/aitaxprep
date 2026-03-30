# Tax Brackets and Rates

> ⚠️ **CRITICAL**: Tax brackets change annually for inflation. You MUST verify these against the [current year IRS Revenue Procedure](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments) before calculating tax.

## How Tax Brackets Work

The U.S. uses a **progressive (marginal) tax system**. Income is taxed in layers:
- Only income WITHIN each bracket is taxed at that bracket's rate
- You don't pay the top rate on all your income

### Example (rates are illustrative — VERIFY current year)
For a single filer with $80,000 taxable income:
```
First $11,600     × 10% =  $1,160
$11,601 - $47,150 × 12% =  $4,266
$47,151 - $80,000 × 22% =  $7,227
                    Total = $12,653
```

## Federal Tax Brackets

⚠️ **DO NOT USE THESE NUMBERS. Fetch current year brackets from the IRS.**

These are provided as structural reference only. The actual thresholds change every year.

### Structure (7 brackets)

| Rate | Single | MFJ | MFS | HOH |
|------|--------|-----|-----|-----|
| 10% | Up to $X | Up to $X | Up to $X | Up to $X |
| 12% | $X - $X | $X - $X | $X - $X | $X - $X |
| 22% | $X - $X | $X - $X | $X - $X | $X - $X |
| 24% | $X - $X | $X - $X | $X - $X | $X - $X |
| 32% | $X - $X | $X - $X | $X - $X | $X - $X |
| 35% | $X - $X | $X - $X | $X - $X | $X - $X |
| 37% | Over $X | Over $X | Over $X | Over $X |

**Where to get current thresholds:**
- [IRS Revenue Procedure (annual)](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments)
- [IRS Tax Rate Schedules](https://www.irs.gov/pub/irs-pdf/i1040gi.pdf)

## Special Tax Rates

### Qualified Dividends and Long-Term Capital Gains

These are taxed at preferential rates (lower than ordinary income):

| Rate | Single | MFJ |
|------|--------|-----|
| 0% | Up to $X | Up to $X |
| 15% | $X - $X | $X - $X |
| 20% | Over $X | Over $X |

**VERIFY thresholds**: [IRS Revenue Procedure](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments)

**When to use**: If Form 1040 Line 3a (qualified dividends) > 0 OR Line 7 (capital gains) > 0, use the **Qualified Dividends and Capital Gain Tax Worksheet** instead of the standard tax table.

### Net Investment Income Tax (NIIT)
- **Rate**: 3.8% on net investment income
- **Threshold**: AGI over $200,000 (Single) or $250,000 (MFJ)
- **Verify**: [Form 8960 Instructions](https://www.irs.gov/instructions/i8960)

### Self-Employment Tax
- **Rate**: 15.3% (12.4% Social Security + 2.9% Medicare) on 92.35% of net SE income
- **Social Security wage base**: Changes annually — VERIFY
- **Deduction**: 50% of SE tax is deductible on Schedule 1
- **Verify**: [Publication 334](https://www.irs.gov/publications/p334)

### Alternative Minimum Tax (AMT)
- Separate tax calculation with fewer deductions
- Exemption amounts change annually
- **Verify**: [Form 6251 Instructions](https://www.irs.gov/instructions/i6251)

## Tax Calculation Process for AI

```
1. Determine taxable income (Form 1040 Line 15)

2. Check: Does the return have qualified dividends (Line 3a > 0)
   OR capital gains (Line 7 > 0)?

   YES → Use Qualified Dividends and Capital Gain Tax Worksheet
   NO  → Use Tax Table (if income < $100,000)
         or Tax Computation Worksheet (if income ≥ $100,000)

3. IMPORTANT: Fetch current year tax brackets from IRS before calculating

4. Apply the marginal rates to each bracket of taxable income

5. Enter result on Form 1040 Line 16
```

## IRS References
- [IRS Tax Inflation Adjustments](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments)
- [Form 1040 Instructions — Tax Computation](https://www.irs.gov/instructions/i1040)
- [Publication 17 — Tax Computation](https://www.irs.gov/publications/p17)
- [Tax Table (PDF)](https://www.irs.gov/pub/irs-pdf/i1040tt.pdf)
