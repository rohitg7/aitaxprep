# Instructions for AI Tools — Document Conversion

You are helping a user convert their tax documents into structured markdown files. Follow these instructions precisely.

## Your Task

1. Install the **markitdown** library (see below) — it is the approved tool for document conversion
2. Use `markitdown` to convert each file in the user's document folder to raw markdown
3. For each converted document, determine its type (W-2, 1099, etc.)
4. Re-structure the raw markdown into the standardized schema for that document type (see below)
5. Save as `{document_type}_{sequence}.md` in the output folder
6. Create a `_index.md` summary file listing all converted documents

## Step 0: Install markitdown (REQUIRED)

Before processing any documents, install Microsoft's **markitdown** library:

```bash
pip install 'markitdown[all]'
```

This is the **only pre-approved library** for document conversion. It handles PDFs, images (OCR), Excel, CSV, Word, HTML, and more.

> ⚠️ **IMPORTANT — Library Policy**:
> - You MUST use `markitdown` for all document conversion.
> - If `markitdown` fails to process a specific file (e.g., unsupported format, corrupted file, poor OCR results), you MUST ask the user for explicit approval before installing or using any alternative library.
> - Do NOT silently install other packages. Always explain what failed, what alternative you propose, and wait for user confirmation.
> - Acceptable reason to ask: "markitdown could not extract text from `scan_blurry.jpg` — may I install `pytesseract` for better OCR? [Y/N]"

## How to Process Each Document

### Step-by-step for each file:

1. **Convert with markitdown**:
   ```bash
   markitdown "path/to/document.pdf" -o "/tmp/raw_output.md"
   ```
   Or in Python:
   ```python
   from markitdown import MarkItDown
   md = MarkItDown()
   result = md.convert("path/to/document.pdf")
   raw_text = result.text_content
   ```

2. **Identify document type** from the raw markdown content:
   - Look for keywords: "Wage and Tax Statement" → W-2, "Interest Income" → 1099-INT, etc.
   - Look for form numbers: "Form W-2", "Form 1099-INT", etc.

3. **Extract fields** from the raw markdown and map them to the structured schema (see Document Schemas below)

4. **Save** as structured markdown following the schema

### Format-Specific Notes

#### PDFs
- `markitdown` extracts text content directly
- If the PDF is a scanned image (no selectable text), markitdown may return minimal content — use the `markitdown-ocr` plugin or ask user for approval to use an alternative

#### Images / Scanned Documents
- `markitdown` supports images with EXIF metadata and basic OCR
- For better OCR results, you can use markitdown with an LLM vision model:
  ```python
  from markitdown import MarkItDown
  from openai import OpenAI
  md = MarkItDown(llm_client=OpenAI(), llm_model="gpt-4o")
  result = md.convert("scanned_w2.jpg")
  ```
- Double-check numbers that are critical (wages, tax amounts, SSNs)
- If markitdown OCR quality is insufficient, ask user: "markitdown could not reliably read [filename]. May I use your AI vision capabilities directly to read this document?"

#### CSV / Excel Files
- `markitdown` converts Excel/CSV to markdown tables directly
- These are typically brokerage/bank statements with transaction details
- Map columns to the appropriate schema fields

#### Word / HTML Documents
- `markitdown` handles these natively
- Extract relevant tax information and map to schema

#### Unknown or Failed Documents
- If `markitdown` fails entirely on a file, report the error to the user
- Ask for approval before trying any alternative approach
- If the document type cannot be determined, use the generic schema

## Formatting Rules

- **SSNs**: Mask as `***-**-XXXX` (show only last 4 digits). Example: `***-**-1234`
- **EINs**: Include in full (employer identification numbers are public)
- **Dollar amounts**: Plain numbers, no `$` or commas. Example: `85000.00` not `$85,000.00`
- **Empty/N/A fields**: Use `0.00` for numbers, leave value cell blank for text
- **Booleans**: Use `true` or `false` (lowercase)
- **Dates**: Use `YYYY-MM-DD` format
- **Metadata comments**: Every file must start with `<!-- schema_version: 1.0 -->` and `<!-- document_type: {type} -->`

## Document Schemas

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

## Quality Checks

After converting all documents, verify:
- All SSNs are consistently masked as `***-**-XXXX`
- All dollar amounts are plain numbers (no `$` or `,`)
- Every source document has a corresponding `.md` file
- The `_index.md` file lists all converted documents with correct types
- No full SSNs appear anywhere in the output files
- All monetary values have exactly 2 decimal places

## Handling Multiple Pages / Multi-Part Documents

- **Multi-page W-2s**: Some W-2s have copies (Copy B, Copy C). They contain the same data — extract once.
- **Consolidated 1099**: Brokerages often send a single document with 1099-INT, 1099-DIV, and 1099-B combined. Create separate markdown files for each type.
- **Multiple accounts at same institution**: Create separate files with incrementing sequence numbers.
