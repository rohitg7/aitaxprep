# Schedule B Instructions — Interest and Ordinary Dividends (AI-Optimized)
<!-- schema_version: 1.0 -->
<!-- last_updated: 2026-03-23 -->

> ⚠️ **IMPORTANT**: These instructions are AI-optimized summaries, not the official IRS instructions. You MUST cross-validate every threshold, rate, and limit against the [official Schedule B instructions](https://www.irs.gov/instructions/i1040sb) before producing a final tax return.

## When to Use This Form

Schedule B is required when **any** of the following are true:
- Total taxable interest income exceeds $1,500
- Total ordinary dividend income exceeds $1,500
- You had a financial interest in, or signature authority over, a foreign financial account (FBAR)
- You received a distribution from, or were a grantor/transferor to, a foreign trust

## Line-by-Line Instructions

### Part I — Interest (Lines 1–4)

#### Line 1: List Each Payer
- **Source**: All 1099-INT forms (Box 1) + any other interest income
- **Format**: List each payer name and amount separately
- **Example**:
  ```
  Chase Bank                    245.67
  Ally Bank                     1302.44
  US Treasury                   500.00
  ```
- **Include**: Interest from banks, credit unions, bonds, seller-financed mortgages, tax refunds
- **Exclude**: Tax-exempt interest (reported separately on 1040 Line 2a)

#### Line 2: Total
- **Calculation**: Sum of all amounts listed on Line 1

#### Line 3: Excludable Interest on Series EE and I Bonds
- **Source**: Form 8815 (if using bonds for qualified education expenses)
- **Note**: Most filers enter 0 here

#### Line 4: Taxable Interest
- **Calculation**: Line 2 - Line 3
- **Flows to**: Form 1040, Line 2b

### Part II — Ordinary Dividends (Lines 5–6)

#### Line 5: List Each Payer
- **Source**: All 1099-DIV forms (Box 1a — total ordinary dividends)
- **Format**: List each payer name and amount separately
- **Example**:
  ```
  Vanguard Total Stock Market   1850.00
  Fidelity 500 Index Fund       675.33
  Apple Inc.                    44.00
  ```

#### Line 6: Total Ordinary Dividends
- **Calculation**: Sum of all amounts listed on Line 5
- **Flows to**: Form 1040, Line 3b

### Part III — Foreign Accounts and Trusts (Lines 7–8)

#### Line 7a: Foreign Financial Accounts (FBAR)
- **Question**: "At any time during the tax year, did you have a financial interest in or a signature or other authority over a financial account (such as a bank account, securities account, or brokerage account) located in a foreign country?"
- **If Yes**: You may need to file **FinCEN Form 114** (FBAR) — this is filed separately with the Financial Crimes Enforcement Network, NOT with the IRS
- **Threshold**: Total aggregate value of all foreign accounts exceeded $10,000 at any time during the year
- **IRS Verification**: [Publication 54](https://www.irs.gov/publications/p54) and [FinCEN BSA E-Filing](https://bsaefiling.fincen.treas.gov/)

#### Line 7b: Foreign Account Countries
- **If Line 7a is Yes**: List the name of each foreign country where accounts are held

#### Line 8: Foreign Trusts
- **Question**: "Did you receive a distribution from, or were you the grantor of, or transferor to, a foreign trust?"
- **If Yes**: May need to file **Form 3520** (Annual Return to Report Transactions with Foreign Trusts)

## Decision Tree

```
Do you have interest income > $1,500 OR dividend income > $1,500?
├── Yes → Schedule B is REQUIRED
│   └── List all payers and amounts in Parts I and II
└── No → Schedule B is OPTIONAL (but still report totals on 1040 Lines 2b and 3b)

Do you have any foreign financial accounts?
├── Yes → Complete Part III
│   ├── Aggregate value > $10,000 at any time? → File FinCEN Form 114 (FBAR)
│   └── Aggregate value > $50,000 at year end (or $75,000 at any time)?
│       └── May need Form 8938 (FATCA) — VERIFY thresholds
└── No → Check "No" on Line 7a
```

## Important Notes

- **Nominee interest/dividends**: If you received a 1099 that includes amounts actually belonging to someone else, list the total on Schedule B, then subtract the nominee portion and report it on a 1099 you file for the actual owner
- **Accrued interest on bonds**: If you paid accrued interest when purchasing a bond, you can subtract it from the interest reported — list it as a negative line item
- **Original Issue Discount (OID)**: Interest from 1099-OID is also reported in Part I
- **Tax-exempt interest** (1099-INT Box 8) is NOT included on Schedule B — it goes only on Form 1040, Line 2a
- **Qualified dividends** (1099-DIV Box 1b) are NOT separately listed on Schedule B — they are a subset of ordinary dividends and reported on Form 1040, Line 3a

## Key IRS Publication References

| Topic | Publication |
|-------|------------|
| Interest income | [Publication 550](https://www.irs.gov/publications/p550) |
| Dividend income | [Publication 550](https://www.irs.gov/publications/p550) |
| Foreign accounts (FBAR) | [FinCEN Form 114 instructions](https://bsaefiling.fincen.treas.gov/) |
| FATCA (Form 8938) | [Form 8938 instructions](https://www.irs.gov/instructions/i8938) |
| Schedule B instructions | [Schedule B instructions](https://www.irs.gov/instructions/i1040sb) |
