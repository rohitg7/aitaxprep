# Tax Return Markdown Schema (v1.0)

This is the canonical format for a completed federal tax return. All AI tools must produce output conforming to this schema.

## Schema Rules

1. **File format**: Standard markdown (`.md`)
2. **Metadata**: HTML comments at the top of the file
3. **Tables**: Markdown tables with `|` separators
4. **Numbers**: Plain decimal numbers without `$` or commas (e.g., `85000.00`)
5. **SSNs**: Masked as `***-**-XXXX`
6. **Line numbers**: Match official IRS form line numbers exactly
7. **Source column**: Document traceability (which source document provided the value)
8. **Sections**: One `## Form/Schedule` heading per IRS form, with `### Section` sub-headings

## Metadata Block

```markdown
# Federal Tax Return {tax_year}
<!-- schema_version: 1.0 -->
<!-- tax_year: 2025 -->
<!-- generated_by: claude-code -->
<!-- generated_date: 2026-03-15 -->
```

Required metadata fields:
- `schema_version` — Version of this schema (currently `1.0`)
- `tax_year` — The tax year being filed (e.g., `2025`)
- `generated_by` — Name of the AI tool that generated this return
- `generated_date` — Date generated in `YYYY-MM-DD` format

## Filing Information Section

```markdown
## Filing Information
| Field | Value |
|-------|-------|
| filing_status | single |
| first_name | John |
| last_name | Doe |
| ssn | ***-**-1234 |
| occupation | Software Engineer |
| address | 123 Main St |
| apt | |
| city | Austin |
| state | TX |
| zip | 78701 |
| phone | 5125550100 |
| email | john@example.com |
```

For joint filers, add:
```markdown
| spouse_first_name | Jane |
| spouse_last_name | Doe |
| spouse_ssn | ***-**-5678 |
| spouse_occupation | Teacher |
```

### Filing Status Values
- `single`
- `married_filing_jointly`
- `married_filing_separately`
- `head_of_household`
- `qualifying_surviving_spouse`

## Dependents Section

```markdown
## Dependents
| name | ssn | relationship | months_lived | child_tax_credit | other_credit |
|------|-----|-------------|-------------|-----------------|-------------|
| Alex Doe | ***-**-9876 | son | 12 | true | false |
| Sam Doe | ***-**-5432 | daughter | 12 | true | false |
```

If no dependents, include the header with an empty table.

## Form Sections

Each IRS form or schedule gets its own `##` heading. Within each form, use `###` for sections.

### Line Item Tables

All line items use this format:

```markdown
| Line | Description | Value | Source |
|------|-------------|-------|--------|
| 1a | Wages, salaries, tips | 85000.00 | W-2: Acme Corp |
```

- **Line**: Exact IRS form line number (e.g., `1a`, `2b`, `15`)
- **Description**: Brief description matching the IRS form
- **Value**: The calculated value (plain number, 2 decimal places)
- **Source**: Where this value came from:
  - Document reference: `W-2: Acme Corp`, `1099-INT: Chase Bank`
  - Calculation: `Sum`, `Line 9 - Line 10`, `Tax table`
  - Cross-form: `Schedule D`, `Schedule 1 Line 10`
  - Verified: `IRS Pub 550 (2025)`

### Values

- **Currency**: `85000.00` (always 2 decimal places, no `$` or commas)
- **Negative values**: `-3000.00` (use minus sign)
- **Zero**: `0.00`
- **Text**: Plain text (no quotes)
- **Boolean**: `true` or `false`
- **Checkbox**: `true` (checked) or `false` (unchecked)

## Form Ordering

Include forms in this order in the markdown file:

1. Filing Information
2. Dependents
3. Form 1040 (main form — always present)
4. Schedule 1 (if applicable)
5. Schedule 2 (if applicable)
6. Schedule 3 (if applicable)
7. Schedule A (if applicable)
8. Schedule B (if applicable)
9. Schedule C (if applicable)
10. Schedule D (if applicable)
11. Schedule E (if applicable)
12. Schedule F (if applicable)
13. Schedule SE (if applicable)
14. Form 8949 (if applicable)
15. Form 8889 (if applicable)
16. Form 8863 (if applicable)
17. Other forms as needed
18. Validation Report (always present, at the end)

## Validation Report Section

Always include this as the last section:

```markdown
## Validation Report

### IRS Sources Consulted
| Check | Status | IRS Source Used |
|-------|--------|----------------|
| Standard deduction verified | ✅ | Rev. Proc. 2025-XX |
| Tax brackets verified | ✅ | Rev. Proc. 2025-XX |
| Form instructions consulted | ✅ | i1040, i1040sd |
| Mid-year changes checked | ✅ | IRS Newsroom YYYY-MM-DD |

### Cross-Form Consistency
| Check | Status |
|-------|--------|
| 1040 Line 1a = sum(W-2 Box 1) | ✅ |
| 1040 Line 2b = sum(1099-INT Box 1) | ✅ |
| 1040 Line 7 = Schedule D Line 21 | ✅ |
| 1040 Line 25a = sum(W-2 Box 2) | ✅ |

### Warnings
- (Any issues requiring human attention)
```

## Example

See [Simple W-2 Return Example](./examples/simple-w2-return/expected-return.md) for a complete, filled-in example.
