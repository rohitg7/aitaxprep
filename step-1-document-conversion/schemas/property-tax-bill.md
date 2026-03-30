# Property Tax Bill — Schema
<!-- schema_version: 1.0 -->
<!-- document_type: property_tax -->

> See [for-ai-tools.md](../for-ai-tools.md) for the full instruction set.

## Schema

```markdown
# Property Tax Bill / Statement
<!-- schema_version: 1.0 -->
<!-- document_type: property_tax -->

## Taxing Authority Information
| Field | Value |
|-------|-------|
| taxing_authority | |
| authority_address | |
| county | |
| state | |

## Property Information
| Field | Value |
|-------|-------|
| property_address | |
| parcel_number | |
| property_type | residential / commercial / land |
| tax_year | |

## Assessment Details
| Field | Value |
|-------|-------|
| assessed_value | |
| land_value | |
| improvement_value | |
| exemptions | |
| net_taxable_value | |
| tax_rate | |

## Tax Amounts
| Field | Value |
|-------|-------|
| total_tax_levied | |
| county_tax | |
| city_tax | |
| school_tax | |
| special_assessments | |
| other_taxes | |

## Payment History
| date | period | amount_paid | payment_method |
|------|--------|-------------|----------------|
| | | | |

## Summary
| Field | Value |
|-------|-------|
| total_property_tax_paid | |
| tax_year | |
```

## Key Fields for Tax Return

| Field | Flows To | Notes |
|-------|----------|-------|
| Total property tax paid | Schedule A, Line 5b (state and local real estate taxes) | Only amounts actually **paid** during the tax year |
| Combined with state/local income or sales tax | Schedule A, Line 5d (total SALT) | Subject to SALT cap |

## SALT Deduction Cap

The total of **all** state and local taxes (SALT) is capped:
- **$10,000** ($5,000 if married filing separately)
- SALT includes: state income tax (or sales tax) + real estate taxes + personal property taxes

> ⚠️ **VERIFY** the SALT cap is still in effect for the current tax year against [IRS Publication 5307](https://www.irs.gov/publications/p5307) and current legislation.

```
Calculate total SALT:
  State/local income tax (or sales tax) [Schedule A Line 5a]
+ Real estate taxes [Schedule A Line 5b]
+ Personal property taxes [Schedule A Line 5c]
= Total SALT

Is total SALT > $10,000 ($5,000 MFS)?
├── Yes → Deduction is limited to $10,000 ($5,000 MFS)
└── No → Deduct full SALT amount
```

## What Is Deductible vs. Not Deductible

| Deductible | NOT Deductible |
|-----------|----------------|
| Ad valorem (value-based) property taxes | Special assessments for local improvements (sidewalks, sewers) |
| State and local real estate taxes | Transfer taxes |
| County, city, school district taxes | Homeowner association (HOA) fees |
| | Utility charges |
| | Trash collection fees (unless based on property value) |

## Triggers

- Property tax paid > 0 → Consider **Schedule A** (itemized deductions)
- Total SALT exceeds cap → Limited deduction on Schedule A Line 5d

## Important Notes

- Only **actual payments** made during the tax year are deductible — not amounts billed or assessed
- If property taxes are paid through a mortgage escrow account, use the amount the escrow company actually paid to the taxing authority
- Property taxes on rental properties are deducted on **Schedule E**, not Schedule A
- Property taxes on business property are deducted on **Schedule C** (or applicable business form), not Schedule A
- Prepaying next year's property tax may not provide a deduction if the tax has not been assessed yet — see [Publication 530](https://www.irs.gov/publications/p530)
- **IRS Verification**: [Publication 530](https://www.irs.gov/publications/p530) — Tax Information for Homeowners
