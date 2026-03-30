# Step 1: Document Conversion

Convert your tax documents (W-2s, 1099s, brokerage statements, etc.) into structured markdown files that AI tools can process for tax return generation.

## Overview

Your AI tool will:
1. Install and use **[markitdown](https://github.com/microsoft/markitdown)** (Microsoft's document-to-markdown converter) to extract raw content from your documents
2. Identify the document type (W-2, 1099-INT, etc.)
3. Re-structure the extracted content into our standardized markdown schema
4. Save one `.md` file per document

## Required Tool: markitdown

We use Microsoft's **markitdown** library as the trusted document conversion tool. It supports PDFs, images (with OCR), Excel, CSV, Word, HTML, and more.

### Installation
```bash
pip install 'markitdown[all]'
```

### Usage
```bash
# Convert a single file
markitdown path-to-file.pdf -o output.md

# Or pipe
cat document.pdf | markitdown
```

> ⚠️ **Library Policy**: `markitdown` is the only pre-approved library for document conversion. If it fails to process a document and the AI agent needs to use a different library, the agent **must ask the user for explicit approval** before installing or using any alternative.

## For AI Tools

→ **[AI Tool Instructions](./for-ai-tools.md)** — Point your AI tool to this page.

## Document Schemas

Each document type has a specific markdown schema:

### Income Documents
| Document | Description | Schema |
|----------|-------------|--------|
| W-2 | Wage and Tax Statement | [w2.md](./schemas/w2.md) |
| 1099-INT | Interest Income | [1099-int.md](./schemas/1099-int.md) |
| 1099-DIV | Dividend Income | [1099-div.md](./schemas/1099-div.md) |
| 1099-B | Brokerage/Capital Gains | [1099-b.md](./schemas/1099-b.md) |
| 1099-R | Retirement Distributions | [1099-r.md](./schemas/1099-r.md) |
| 1099-NEC | Non-Employee Compensation | [1099-nec.md](./schemas/1099-nec.md) |
| 1099-MISC | Miscellaneous Income | [1099-misc.md](./schemas/1099-misc.md) |
| 1099-G | Government Payments | [1099-g.md](./schemas/1099-g.md) |
| SSA-1099 | Social Security Benefits | [ssa-1099.md](./schemas/ssa-1099.md) |
| K-1 | Partner/S-Corp Income | [k1.md](./schemas/k1.md) |

### Deduction/Credit Documents
| Document | Description | Schema |
|----------|-------------|--------|
| 1098 | Mortgage Interest | [1098.md](./schemas/1098.md) |
| 1098-T | Tuition Statement | [1098-t.md](./schemas/1098-t.md) |
| 1098-E | Student Loan Interest | [1098-e.md](./schemas/1098-e.md) |
| Charitable Receipt | Donation Records | [charitable-receipt.md](./schemas/charitable-receipt.md) |
| Property Tax Bill | Property Tax Records | [property-tax-bill.md](./schemas/property-tax-bill.md) |

### Other
| Document | Description | Schema |
|----------|-------------|--------|
| Brokerage Statement | Annual brokerage summary | [brokerage-statement.md](./schemas/brokerage-statement.md) |
| Bank Statement | Interest summary | [bank-statement.md](./schemas/bank-statement.md) |
| Generic | Unknown document type | [generic.md](./schemas/generic.md) |

## Output Format

All document markdown files follow these conventions:

### File Naming
```
docs_md/
├── _index.md              # Summary of all converted documents
├── {type}_{sequence}.md   # One file per document
```

**Naming rules:**
- Use lowercase document type: `w2`, `1099_int`, `1099_div`, `1099_b`, `1098`, `charitable`, etc.
- Sequence number starting at 1: `w2_1.md`, `w2_2.md` (if multiple W-2s)
- Unknown documents: `unknown_1.md`

### Common Rules
- **SSN masking**: Always use `***-**-XXXX` format (mask first 5 digits)
- **Numbers**: Plain decimal numbers without `$` or commas: `85000.00` not `$85,000.00`
- **Empty fields**: Use `0.00` for numeric fields, leave blank for text fields
- **Booleans**: Use `true` or `false`
- **Dates**: Use `YYYY-MM-DD` format
- **Tables**: Use markdown tables with `|` separators
- **Metadata**: Include `schema_version` and `document_type` as HTML comments

### Index File (_index.md)
```markdown
# Document Conversion Summary
<!-- generated_date: 2026-03-15 -->
<!-- document_count: 5 -->

| # | File | Type | Description |
|---|------|------|-------------|
| 1 | w2_1.md | W-2 | Acme Corporation - wages |
| 2 | 1099_int_1.md | 1099-INT | Chase Bank - interest |
| 3 | 1099_div_1.md | 1099-DIV | Vanguard - dividends |
| 4 | 1099_b_1.md | 1099-B | Schwab - stock sales |
| 5 | charitable_1.md | Charitable | Various donations |
```

## Examples

→ [W-2 Example](./examples/w2-example.md)
→ [1099-INT Example](./examples/1099-int-example.md)
