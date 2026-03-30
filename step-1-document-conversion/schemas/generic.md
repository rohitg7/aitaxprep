# Generic / Unknown Tax Document — Schema
<!-- schema_version: 1.0 -->
<!-- document_type: unknown -->

> See [for-ai-tools.md](../for-ai-tools.md) for the full instruction set.

## When to Use

Use this schema when the document type cannot be identified as one of the specific schemas (W-2, 1099, 1098, etc.). This ensures all extractable data is captured for manual review.

## Schema

```markdown
# Unknown Tax Document
<!-- schema_version: 1.0 -->
<!-- document_type: unknown -->

## Document Information
| Field | Value |
|-------|-------|
| document_title | |
| issuer | |
| issuer_tin | |
| issuer_address | |
| date | |
| tax_year | |

## Recipient Information
| Field | Value |
|-------|-------|
| recipient_name | |
| ssn | ***-**-XXXX |
| recipient_address | |

## Extracted Data
| Field | Value |
|-------|-------|
| | |

## Dollar Amounts
| Description | Amount |
|-------------|--------|
| | |

## Raw Text
(Include the full extracted text for manual review)
```

## Key Fields for Tax Return

This document type has no predefined flow to tax forms. After extraction, the data should be reviewed manually to determine:

1. What type of income, deduction, or credit the document supports
2. Which tax form or schedule the data flows to
3. Whether the amounts are taxable or informational

## Processing Guidelines

When encountering an unknown document:

1. **Extract all text** — preserve the full content in the Raw Text section
2. **Identify dollar amounts** — list every monetary value found in the Dollar Amounts table
3. **Look for clues** — check for:
   - IRS form numbers or references
   - Tax-related keywords (income, withholding, deduction, credit, basis, etc.)
   - EIN or TIN numbers that indicate an issuing entity
   - Tax year references
4. **Flag for review** — mark the document as needing human review in the `_index.md` file

## Common Unrecognized Documents

| Document | Likely Type | Suggested Action |
|----------|------------|------------------|
| Year-end brokerage statement | May contain 1099-B, 1099-DIV, 1099-INT | Split into separate schemas |
| Employer stock plan statement | May relate to W-2 Box 12 or 1099-B | Cross-reference with W-2 |
| Health insurance form (1095-A/B/C) | Health coverage documentation | Generally informational; 1095-A needed for Form 8962 |
| Foreign income statement | May need Form 1116 or Form 2555 | Consult foreign income rules |
| State tax document | State-specific | Handle in state return |
| Estimated tax payment receipts | Form 1040, Line 26 | Record payment amounts and dates |
| Prior year carryover statement | Various (capital losses, NOL, etc.) | Apply to current year calculations |
