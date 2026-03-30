# Charitable Donation Receipt — Schema
<!-- schema_version: 1.0 -->
<!-- document_type: charitable -->

> See [for-ai-tools.md](../for-ai-tools.md) for the full instruction set.

## Schema

```markdown
# Charitable Donation Receipt
<!-- schema_version: 1.0 -->
<!-- document_type: charitable -->

## Organization Information
| Field | Value |
|-------|-------|
| organization_name | |
| ein | |
| organization_address | |
| is_501c3 | true/false |

## Donor Information
| Field | Value |
|-------|-------|
| donor_name | |

## Donations
| date | description | type | value | goods_or_services_provided | fair_market_value |
|------|-------------|------|-------|---------------------------|-------------------|
| | | cash | | none | |

## Summary
| Field | Value |
|-------|-------|
| total_cash_donations | |
| total_noncash_donations | |
| total_donations | |
```

## Key Fields for Tax Return

| Field | Flows To | Notes |
|-------|----------|-------|
| Total cash donations | Schedule A, Line 12 (gifts by cash or check) | Subject to AGI percentage limits |
| Total noncash donations | Schedule A, Line 13 (other than cash or check) | Fair market value |
| Noncash donations > 500.00 total | **Form 8283** (Noncash Charitable Contributions) | Required for total noncash > $500 |
| Single noncash item > 5000.00 | Form 8283, Section B + qualified appraisal | Requires independent appraisal |
| Cash donation ≥ 250.00 | Must have written acknowledgment from charity | Contemporaneous written acknowledgment |

## Charitable Contribution Limits (% of AGI)

| Donation Type | To Public Charities | To Private Foundations |
|--------------|--------------------|-----------------------|
| Cash | 60% of AGI | 30% of AGI |
| Capital gain property | 30% of AGI | 20% of AGI |
| Ordinary income property | 50% of AGI | 30% of AGI |

> ⚠️ **VERIFY** these AGI percentage limits against [Publication 526](https://www.irs.gov/publications/p526) for the current tax year.

## Carryover Rules

- Contributions exceeding the AGI limit can be carried forward for **5 years**
- Carryover amounts are reported on Schedule A, Line 14

## Substantiation Requirements

```
Donation < $250
├── Cash → Bank record, receipt, or written communication from charity
└── Noncash → Receipt from charity + records of fair market value

Donation ≥ $250
├── Cash → Written acknowledgment from charity (must state no goods/services
│          were provided, or describe and value goods/services provided)
└── Noncash → Written acknowledgment + Form 8283 if total noncash > $500

Single noncash item > $5,000
└── Qualified appraisal required + Form 8283, Section B
```

## Triggers

- Any charitable donations → Consider **Schedule A** (itemized deductions)
- Total noncash donations > 500.00 → **Form 8283** required
- Single noncash item > 5000.00 → **Form 8283, Section B** + qualified appraisal
- Total contributions > AGI percentage limit → Carryover to next year

## Important Notes

- Charitable deductions are only available to taxpayers who **itemize** on Schedule A
- Donations to individuals, political organizations, or candidates are NOT deductible
- Verify the organization's 501(c)(3) status using the [IRS Tax Exempt Organization Search](https://www.irs.gov/charities-non-profits/tax-exempt-organization-search)
- Quid pro quo contributions: If goods/services were received, only the amount exceeding their fair market value is deductible
- **IRS Verification**: [Publication 526](https://www.irs.gov/publications/p526) — Charitable Contributions
