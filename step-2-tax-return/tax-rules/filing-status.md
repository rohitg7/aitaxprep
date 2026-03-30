# Filing Status Determination

> ⚠️ **Verify against** [IRS Publication 17, Chapter 2](https://www.irs.gov/publications/p17#en_US_2024_publink1000170768) and [Form 1040 Instructions](https://www.irs.gov/instructions/i1040) for the current tax year.

## Filing Status Options

| Status | Code | Description |
|--------|------|-------------|
| Single | `single` | Unmarried, or legally separated/divorced on Dec 31 |
| Married Filing Jointly | `married_filing_jointly` | Married on Dec 31, filing one return together |
| Married Filing Separately | `married_filing_separately` | Married on Dec 31, each filing their own return |
| Head of Household | `head_of_household` | Unmarried + paid >50% of household costs + qualifying person |
| Qualifying Surviving Spouse | `qualifying_surviving_spouse` | Spouse died within prior 2 years + dependent child |

## Decision Tree

```
As of December 31 of the tax year, are you legally married?
│
├── YES
│   ├── Do you want to file a joint return with your spouse?
│   │   ├── YES → married_filing_jointly
│   │   └── NO → married_filing_separately
│   │       NOTE: MFJ almost always results in lower tax.
│   │       MFS loses access to many credits (EITC, education credits, etc.)
│   │
│   └── Did your spouse die during the tax year?
│       └── YES → You can still file married_filing_jointly for that year
│
├── NO (unmarried, divorced, or legally separated on Dec 31)
│   ├── Did your spouse die in one of the two prior tax years?
│   │   ├── YES → Do you have a dependent child who lived with you all year?
│   │   │   ├── YES → qualifying_surviving_spouse
│   │   │   └── NO → single (or head_of_household if qualified)
│   │   └── NO ↓
│   │
│   ├── Do you have a qualifying person (child, dependent parent, etc.)?
│   │   ├── YES → Did you pay more than 50% of the cost of keeping up a home?
│   │   │   ├── YES → head_of_household
│   │   │   └── NO → single
│   │   └── NO → single
│   └──
│
└── SPECIAL CASES
    ├── Considered unmarried: If you lived apart from spouse for last 6 months
    │   of the year AND have a dependent child → may qualify as head_of_household
    └── Nonresident alien spouse: May be able to file MFJ with election
```

## Qualifying Person for Head of Household

A qualifying person is:
- Your unmarried child, stepchild, or foster child who lived with you more than half the year
- Your married child who you can claim as a dependent
- Your dependent parent (does NOT need to live with you)
- Other dependent relative who lived with you more than half the year

## Impact on Standard Deduction and Tax Brackets

Filing status affects:
1. **Standard deduction amount** — HOH and MFJ get higher deductions
2. **Tax bracket thresholds** — MFJ brackets are roughly 2x Single
3. **Credit eligibility** — Many credits unavailable if MFS
4. **IRA deduction** — Phase-out ranges differ by status

**Always verify current year amounts**: [IRS Tax Inflation Adjustments](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments)
