# Standard vs. Itemized Deductions

> ⚠️ **Verify standard deduction amounts** against the [current year IRS Revenue Procedure](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments). Amounts change annually for inflation.

## Decision Rule

**Use whichever is LARGER:**
- Standard deduction for your filing status, OR
- Total itemized deductions (Schedule A, Line 17)

### Exception
If you are **Married Filing Separately** and your spouse itemizes, you **must** itemize too (even if your itemized total is less than the standard deduction).

## Standard Deduction Amounts

⚠️ **VERIFY these amounts for the filing tax year. They change annually.**

| Filing Status | Standard Deduction (verify) |
|--------------|---------------------------|
| Single | Check IRS Rev. Proc. |
| Married Filing Jointly | Check IRS Rev. Proc. |
| Married Filing Separately | Check IRS Rev. Proc. |
| Head of Household | Check IRS Rev. Proc. |
| Qualifying Surviving Spouse | Same as MFJ |

### Additional Amounts
- **Age 65 or older**: Add additional amount per person (verify IRS)
- **Blind**: Add additional amount per person (verify IRS)
- Additional amounts are higher for Single/HOH than for MFJ/MFS

## Common Itemized Deductions (Schedule A)

| Category | What Counts | Limits |
|----------|-------------|--------|
| Medical/Dental | Unreimbursed medical expenses | Only amount exceeding 7.5% of AGI |
| State/Local Taxes (SALT) | Income tax OR sales tax + property tax | Capped at $10,000 ($5,000 if MFS) |
| Mortgage Interest | Interest on acquisition debt | Up to $750K of mortgage debt ($375K MFS) |
| Charitable Contributions | Cash + noncash to qualified orgs | Cash: up to 60% of AGI; Noncash: up to 30% |
| Casualty/Theft Losses | From federally declared disasters only | Exceeding $100 per event + 10% of AGI |

## Decision Process for AI

```
1. Look up the standard deduction for the taxpayer's filing status and age
   (VERIFY against current year IRS Rev. Proc.)

2. Calculate potential itemized deductions:
   a. Medical expenses that exceed 7.5% of AGI (from medical receipts)
   b. State/local taxes paid (from W-2 Box 17, property tax bills)
      → Cap at $10,000 ($5,000 if MFS)
   c. Mortgage interest (from 1098 Box 1)
   d. Charitable contributions (from donation receipts)
   e. Any other qualifying deductions

3. Sum all itemized deductions

4. Compare:
   If itemized total > standard deduction → USE SCHEDULE A (itemize)
   If standard deduction > itemized total → USE STANDARD DEDUCTION
   If MFS and spouse itemizes → MUST USE SCHEDULE A

5. Enter the chosen amount on Form 1040 Line 12
```

## Common Scenarios

### Likely to Itemize
- Large mortgage (interest > $10,000+)
- High state income tax states (CA, NY, NJ) — but capped at $10,000
- Significant charitable donations
- Large unreimbursed medical expenses

### Likely to Use Standard Deduction
- Renters with no mortgage
- Low-tax states (TX, FL, WA, NV)
- Low charitable contributions
- No significant medical expenses

## IRS References
- [Publication 17, Chapter 21 — Standard Deduction](https://www.irs.gov/publications/p17)
- [Schedule A Instructions](https://www.irs.gov/instructions/i1040sa)
- [Publication 526 — Charitable Contributions](https://www.irs.gov/publications/p526)
- [Publication 936 — Home Mortgage Interest](https://www.irs.gov/publications/p936)
