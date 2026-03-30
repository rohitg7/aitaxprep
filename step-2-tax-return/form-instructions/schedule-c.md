# Schedule C Instructions — Profit or Loss From Business (AI-Optimized)
<!-- schema_version: 1.0 -->
<!-- last_updated: 2026-03-23 -->

> ⚠️ **IMPORTANT**: These instructions are AI-optimized summaries, not the official IRS instructions. You MUST cross-validate every threshold, rate, and limit against the [official Schedule C instructions](https://www.irs.gov/instructions/i1040sc) and [current year IRS inflation adjustments](https://www.irs.gov/newsroom/irs-provides-tax-inflation-adjustments) before producing a final tax return.

## When to Use This Form

Use Schedule C to report income or loss from a business you operated as a **sole proprietor** or **single-member LLC** (disregarded entity). File Schedule C if:
- You received 1099-NEC for nonemployee compensation
- You had self-employment income from freelance or gig work
- You operated a business as a sole proprietor
- You were a statutory employee (W-2 Box 13 checked)

## Line-by-Line Instructions

### Business Information (Lines A–J)

#### Line A: Principal Business or Profession
- **Enter**: Description of your business activity (e.g., "Software development", "Consulting", "Rideshare driver")

#### Line B: Business Activity Code
- **Source**: [IRS Principal Business Codes](https://www.irs.gov/instructions/i1040sc) — look up the 6-digit NAICS code
- **Example**: 541511 (Custom Computer Programming Services), 711510 (Independent Artists/Writers)

#### Line C: Business Name
- **Enter**: Your business name (if different from your personal name)

#### Line D: Employer ID Number (EIN)
- **Enter**: EIN if you have one (not required for sole proprietors with no employees)

#### Lines E–J: Address, Accounting Method, etc.
- **Line F**: Accounting method — most sole proprietors use **Cash**
- **Line G**: Did you "materially participate" in the business? → Usually **Yes** for active businesses
- **Line I**: If "Yes", you started or acquired this business during the tax year
- **Line J**: If "Yes", you made payments that would require you to file Form(s) 1099

### Income (Lines 1–7)

#### Line 1: Gross Receipts or Sales
- **Source**: Sum of all 1099-NEC Box 1 amounts + other business income
- **Include**: All income from the business activity, whether or not reported on a 1099

#### Line 2: Returns and Allowances
- **Enter**: Any refunds given to clients/customers

#### Line 3: Subtract Line 2 from Line 1
- **Calculation**: Line 1 - Line 2

#### Line 4: Cost of Goods Sold (from Line 42)
- **Source**: Part III (Cost of Goods Sold) — only if you sell products
- **Note**: Most service-based businesses enter 0

#### Line 5: Gross Profit
- **Calculation**: Line 3 - Line 4

#### Line 6: Other Income
- **Include**: Interest on business accounts, scrap sales, bad debts recovered, etc.

#### Line 7: Gross Income
- **Calculation**: Line 5 + Line 6

### Expenses (Lines 8–27)

#### Common Business Expenses

| Line | Description | Examples |
|------|-------------|---------|
| 8 | Advertising | Website ads, business cards, online marketing |
| 9 | Car and truck expenses | Use actual expenses or standard mileage rate (VERIFY rate) |
| 10 | Commissions and fees | Subcontractor payments, platform fees |
| 11 | Contract labor | Payments to non-employees for services |
| 12 | Depletion | Natural resource depletion |
| 13 | Depreciation and section 179 | Business equipment (Form 4562) |
| 14 | Employee benefit programs | Health insurance for employees (not yourself) |
| 15 | Insurance | Business liability, professional, property insurance |
| 16a | Mortgage interest | On business property |
| 16b | Other interest | Business loans, credit line interest |
| 17 | Legal and professional services | Attorney, accountant, tax preparation (business portion) |
| 18 | Office expense | Office supplies, postage, software subscriptions |
| 19 | Pension and profit-sharing plans | Employer contributions to employee plans |
| 20a | Rent — vehicles, machinery, equipment | |
| 20b | Rent — other business property | Office rent, coworking space |
| 21 | Repairs and maintenance | Equipment repair, maintenance |
| 22 | Supplies | Materials consumed in the business |
| 23 | Taxes and licenses | Business licenses, business property tax (NOT income tax) |
| 24a | Travel | Business travel (airfare, hotel, car rental) — must be away from tax home overnight |
| 24b | Deductible meals | Business meals — generally 50% deductible (VERIFY current percentage) |
| 25 | Utilities | Phone, internet, electricity (business portion) |
| 26 | Wages | Payments to employees (not yourself) |
| 27a | Other expenses | See Line 48 (Part V — Other Expenses list) |

> ⚠️ **VERIFY** the standard mileage rate for the current tax year against [IRS standard mileage rates](https://www.irs.gov/tax-professionals/standard-mileage-rates). The rate changes annually.

#### Line 28: Total Expenses
- **Calculation**: Sum of Lines 8 through 27

### Net Profit or Loss (Lines 29–31)

#### Line 29: Tentative Profit (or Loss)
- **Calculation**: Line 7 - Line 28

#### Line 30: Business Use of Home
- **Source**: Form 8829 (Expenses for Business Use of Your Home) or the **Simplified Method**
- **Simplified method**: $5.00 per square foot of home used for business, up to 300 sq ft = max $1,500 (VERIFY)
- **Note**: Home office must be used **regularly and exclusively** for business

#### Line 31: Net Profit or (Loss)
- **Calculation**: Line 29 - Line 30
- **If profit**: Report on Schedule 1, Line 3 → flows to Form 1040, Line 8
- **If loss**: See at-risk rules (Line 32) — may be limited

### Simplified Method for Home Office

```
Do you use part of your home regularly and exclusively for business?
├── No → No home office deduction
└── Yes → Choose a method:
    ├── Simplified Method:
    │   └── $5 × square feet used (max 300 sq ft) = max $1,500
    │   └── Enter on Schedule C, Line 30 (no Form 8829 needed)
    └── Regular Method:
        └── Calculate actual expenses × business percentage
        └── File Form 8829
        └── Enter result on Schedule C, Line 30
```

## Where Schedule C Results Flow

| Schedule C Line | Flows To |
|----------------|----------|
| Line 31 (net profit) | Schedule 1, Line 3 → Form 1040, Line 8 |
| Line 31 (net profit > 400) | **Schedule SE** (self-employment tax) |
| Net profit | **Form 8995** (Qualified Business Income Deduction — 20%) |
| SE tax × 50% | Schedule 1, Line 15 (deductible part of SE tax) |

## Triggers

- Net profit > 400.00 → **Schedule SE** required
- Net profit > 0 → Consider **Form 8995** (QBI deduction)
- Business use of home → **Form 8829** (or simplified method on Line 30)
- Depreciation/section 179 → **Form 4562**
- Contract labor ≥ 600.00 to any individual → You must file **1099-NEC** for that person

## Important Notes

- **Separate Schedule C for each business**: If you operate multiple distinct businesses, file a separate Schedule C for each
- **Hobby vs. business**: If the activity is not engaged in for profit, losses may not be deductible — see [Publication 535](https://www.irs.gov/publications/p535)
- **Self-employed health insurance**: NOT deducted on Schedule C — instead deducted on Schedule 1, Line 17
- **Retirement contributions** (SEP, SIMPLE, solo 401k): NOT on Schedule C — deducted on Schedule 1, Line 16
- **IRS Verification**: [Publication 334](https://www.irs.gov/publications/p334) — Tax Guide for Small Business

## Key IRS Publication References

| Topic | Publication |
|-------|------------|
| Small business tax guide | [Publication 334](https://www.irs.gov/publications/p334) |
| Business expenses | [Publication 535](https://www.irs.gov/publications/p535) |
| Car expenses / mileage | [Publication 463](https://www.irs.gov/publications/p463) |
| Home office | [Publication 587](https://www.irs.gov/publications/p587) |
| Depreciation | [Publication 946](https://www.irs.gov/publications/p946) |
| Schedule C instructions | [Schedule C Instructions](https://www.irs.gov/instructions/i1040sc) |
