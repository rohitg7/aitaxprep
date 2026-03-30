---
layout: default
title: "Step 1: Document Conversion — AI Instructions"
---

<!-- THIS PAGE IS FOR AI TOOLS. Humans: see the [overview](./index.md) instead. -->

# Document Conversion — Instructions for AI Agents

> ⚠️ **DISCLAIMER**: These instructions are AI-generated and not verified by any CPA, tax professional, or the IRS. Output may contain errors. The user is solely responsible for reviewing all converted documents for accuracy.

## ROLE
You are converting tax documents to structured markdown.

## INPUTS
- `{input_dir}`: folder of tax documents (PDF, image, CSV, Excel, Word)
- `{output_dir}`: folder for structured markdown output

## REQUIRED TOOL
```
pip install 'markitdown[all]'
```
markitdown is the ONLY approved conversion library.
- IF markitdown fails on a file → ASK user before installing alternatives
- DO NOT silently install other packages

## PROCEDURE
FOR each file in `{input_dir}`:
1. RUN: `markitdown "{file}" -o "/tmp/raw.md"` OR use Python API:
   ```python
   from markitdown import MarkItDown
   result = MarkItDown().convert("{file}")
   raw = result.text_content
   ```
2. IDENTIFY document type from content (see TYPE DETECTION below)
3. EXTRACT fields → map to schema (see SCHEMAS below)
4. SAVE as `{output_dir}/{type}_{seq}.md`

AFTER all files:
5. CREATE `{output_dir}/_index.md` listing all converted documents

## TYPE DETECTION
| Pattern in Content | Document Type | Output Prefix |
|---|---|---|
| "Wage and Tax Statement" OR "Form W-2" | W-2 | w2 |
| "Interest Income" OR "Form 1099-INT" | 1099-INT | 1099_int |
| "Dividends" OR "Form 1099-DIV" | 1099-DIV | 1099_div |
| "Proceeds from Broker" OR "Form 1099-B" | 1099-B | 1099_b |
| "Nonemployee Compensation" OR "1099-NEC" | 1099-NEC | 1099_nec |
| "Mortgage Interest" OR "Form 1098" | 1098 | 1098 |
| "Charitable" OR "Donation Receipt" | Charitable | charitable |
| "Retirement" OR "Form 1099-R" | 1099-R | 1099_r |
| "Social Security" OR "SSA-1099" | SSA-1099 | ssa_1099 |
| (none match) | Unknown | generic |

## FORMAT RULES
- SSN: mask as `***-**-XXXX` (last 4 only)
- EIN: include in full
- Dollar amounts: plain number, 2 decimals, no $ or commas → `85000.00`
- Empty numbers: `0.00`
- Booleans: `true` / `false`
- Dates: `YYYY-MM-DD`
- Every file MUST start with:
  ```
  <!-- schema_version: 1.0 -->
  <!-- document_type: {type} -->
  ```

## FORMAT-SPECIFIC NOTES
| Format | Notes |
|---|---|
| PDF (text) | markitdown extracts directly |
| PDF (scanned) | May return minimal content. Use LLM vision: `MarkItDown(llm_client=OpenAI(), llm_model="gpt-4o")` |
| Images | Use LLM vision for OCR. Double-check critical numbers. |
| CSV/Excel | markitdown converts to tables. Map columns to schema. |
| Word/HTML | markitdown handles natively |
| Unknown/Failed | Report error. ASK user before trying alternatives. |

## SCHEMAS

### W-2: Wage and Tax Statement

```markdown
# W-2: Wage and Tax Statement
<!-- schema_version: 1.0 -->
<!-- document_type: w2 -->

## Employer Information
| Field | Value |
|-------|-------|
| employer_name | |
| ein | |
| employer_address | |

## Employee Information
| Field | Value |
|-------|-------|
| employee_name | |
| ssn | |
| employee_address | |

## Compensation
| Box | Description | Value |
|-----|-------------|-------|
| 1 | Wages, salaries, tips | |
| 2 | Federal income tax withheld | |
| 3 | Social security wages | |
| 4 | Social security tax withheld | |
| 5 | Medicare wages and tips | |
| 6 | Medicare tax withheld | |
| 7 | Social security tips | |
| 8 | Allocated tips | |
| 10 | Dependent care benefits | |
| 11 | Nonqualified plans | |
| 12a_code | Code | |
| 12a_amount | Amount | |
| 12b_code | Code | |
| 12b_amount | Amount | |
| 12c_code | Code | |
| 12c_amount | Amount | |
| 12d_code | Code | |
| 12d_amount | Amount | |
| 13_statutory_employee | Statutory employee | |
| 13_retirement_plan | Retirement plan | |
| 13_third_party_sick_pay | Third-party sick pay | |
| 14 | Other | |

## State Information
| Field | Value |
|-------|-------|
| state | |
| state_id | |
| state_wages | |
| state_tax | |
| local_wages | |
| local_tax | |
| locality_name | |
```

### 1099-INT: Interest Income

```markdown
# 1099-INT: Interest Income
<!-- schema_version: 1.0 -->
<!-- document_type: 1099_int -->

## Payer Information
| Field | Value |
|-------|-------|
| payer_name | |
| payer_tin | |
| payer_address | |

## Recipient Information
| Field | Value |
|-------|-------|
| recipient_name | |
| ssn | |

## Interest Income
| Box | Description | Value |
|-----|-------------|-------|
| 1 | Interest income | |
| 2 | Early withdrawal penalty | |
| 3 | Interest on U.S. savings bonds and Treasury obligations | |
| 4 | Federal income tax withheld | |
| 5 | Investment expenses | |
| 6 | Foreign tax paid | |
| 7 | Foreign country or U.S. possession | |
| 8 | Tax-exempt interest | |
| 9 | Specified private activity bond interest | |
| 10 | Market discount | |
| 11 | Bond premium | |
| 12 | Bond premium on Treasury obligations | |
| 13 | Bond premium on tax-exempt bond | |
| 14 | Tax-exempt and tax credit bond CUSIP no. | |
| 15 | State | |
| 16 | State identification no. | |
| 17 | State tax withheld | |
```

### 1099-DIV: Dividend Income

```markdown
# 1099-DIV: Dividend Income
<!-- schema_version: 1.0 -->
<!-- document_type: 1099_div -->

## Payer Information
| Field | Value |
|-------|-------|
| payer_name | |
| payer_tin | |
| payer_address | |

## Recipient Information
| Field | Value |
|-------|-------|
| recipient_name | |
| ssn | |

## Dividends
| Box | Description | Value |
|-----|-------------|-------|
| 1a | Total ordinary dividends | |
| 1b | Qualified dividends | |
| 2a | Total capital gain distributions | |
| 2b | Unrecaptured section 1250 gain | |
| 2c | Section 1202 gain | |
| 2d | Collectibles (28%) gain | |
| 2e | Section 897 ordinary dividends | |
| 2f | Section 897 capital gain | |
| 3 | Nondividend distributions | |
| 4 | Federal income tax withheld | |
| 5 | Section 199A dividends | |
| 6 | Investment expenses | |
| 7 | Foreign tax paid | |
| 8 | Foreign country or U.S. possession | |
| 9 | Cash liquidation distributions | |
| 10 | Noncash liquidation distributions | |
| 11 | FATCA filing requirement | |
| 12 | Exempt-interest dividends | |
| 13 | Specified private activity bond interest dividends | |
| 14 | State | |
| 15 | State identification no. | |
| 16 | State tax withheld | |
```

### 1099-B: Proceeds from Broker Transactions

```markdown
# 1099-B: Proceeds from Broker and Barter Exchange Transactions
<!-- schema_version: 1.0 -->
<!-- document_type: 1099_b -->

## Broker Information
| Field | Value |
|-------|-------|
| broker_name | |
| broker_tin | |
| broker_address | |

## Recipient Information
| Field | Value |
|-------|-------|
| recipient_name | |
| ssn | |

## Transactions Summary
| Field | Value |
|-------|-------|
| reporting_category | |
| basis_reported_to_irs | |

## Transactions
| description | date_acquired | date_sold | proceeds | cost_basis | market_discount | wash_sale_loss | gain_loss | short_or_long | basis_reported |
|------------|--------------|-----------|----------|-----------|-----------------|---------------|-----------|--------------|----------------|
| | | | | | | | | | |
```

### 1099-NEC: Nonemployee Compensation

```markdown
# 1099-NEC: Nonemployee Compensation
<!-- schema_version: 1.0 -->
<!-- document_type: 1099_nec -->

## Payer Information
| Field | Value |
|-------|-------|
| payer_name | |
| payer_tin | |
| payer_address | |

## Recipient Information
| Field | Value |
|-------|-------|
| recipient_name | |
| ssn | |

## Compensation
| Box | Description | Value |
|-----|-------------|-------|
| 1 | Nonemployee compensation | |
| 4 | Federal income tax withheld | |
| 5 | State tax withheld | |
| 6 | State/Payer's state no. | |
| 7 | State income | |
```

### 1098: Mortgage Interest Statement

```markdown
# 1098: Mortgage Interest Statement
<!-- schema_version: 1.0 -->
<!-- document_type: 1098 -->

## Lender Information
| Field | Value |
|-------|-------|
| lender_name | |
| lender_tin | |
| lender_address | |

## Borrower Information
| Field | Value |
|-------|-------|
| borrower_name | |
| ssn | |
| property_address | |

## Mortgage Interest
| Box | Description | Value |
|-----|-------------|-------|
| 1 | Mortgage interest received | |
| 2 | Outstanding mortgage principal | |
| 3 | Mortgage origination date | |
| 4 | Refund of overpaid interest | |
| 5 | Mortgage insurance premiums | |
| 6 | Points paid on purchase of principal residence | |
| 7 | Is property address same as borrower address | |
| 8 | Property address (if different) | |
| 9 | Number of mortgaged properties | |
| 10 | Other | |
| 11 | Mortgage acquisition date | |
```

### Charitable Donation Receipt

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
| is_501c3 | |

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

### Generic Document (Unknown Type)

```markdown
# Unknown Tax Document
<!-- schema_version: 1.0 -->
<!-- document_type: unknown -->

## Document Information
| Field | Value |
|-------|-------|
| document_title | |
| issuer | |
| date | |
| tax_year | |

## Extracted Data
| Field | Value |
|-------|-------|
| | |

## Raw Text
(Include the full extracted text for manual review)
```

## MULTI-DOCUMENT RULES
- Multi-page W-2 copies (B, C) → same data, extract once
- Consolidated 1099 → split into separate files per type
- Multiple accounts at same institution → increment sequence number

## QUALITY CHECKS
BEFORE returning to user, verify:
- [ ] All SSNs masked as `***-**-XXXX`
- [ ] All dollar amounts: plain numbers, 2 decimals
- [ ] Every source document has a `.md` file
- [ ] `_index.md` lists all documents
- [ ] No full SSNs anywhere in output
