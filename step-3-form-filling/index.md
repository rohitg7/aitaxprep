# Step 3: Form Filling with Playwright

> 📝 **This step is optional.** The primary value of AI Tax Prep is understanding your taxes (Steps 1 & 2). This step is for advanced users who want to auto-fill IRS Free File Fillable Forms using the generated tax data.

> ⚠️ **DISCLAIMER**: This tool is developed entirely by AI and has not been reviewed or verified by any CPA, tax professional, the IRS, or any other authority. This is for educational and informational purposes only. This is not tax advice. You use this tool entirely at your own risk and are solely responsible for reviewing all filled values before submitting.

Automatically fill your tax return on[FreeFileFillableForms.com](https://www.freefilefillableforms.com/) using the `aitaxprep` CLI tool.

## Overview

The Playwright form filler:
1. Parses your `tax_return.md` file
2. Opens a real browser (you can see everything)
3. Navigates to FreeFileFillableForms.com
4. Waits for you to log in
5. Fills in all form fields automatically
6. Pauses for you to review before submitting
7. **Never auto-submits** — you always click Submit manually

## Installation

```bash
npm install -g aitaxprep
```

Requires Node.js 18+.

## Usage

### Validate First
```bash
tax-filler validate --input ./tax_return.md
```

Checks your markdown for:
- Schema compliance
- Required fields
- Mathematical consistency
- Cross-form references

### Preview
```bash
tax-filler preview --input ./tax_return.md
```

Shows which forms will be filled and a summary of values without opening a browser.

### Fill Forms
```bash
tax-filler fill --input ./tax_return.md
```

Options:
- `--browser chromium|firefox` — Browser to use (default: chromium)
- `--headed` — Show browser window (default: true, always recommended)
- `--pause-before-submit` — Pause after filling (default: true)

### Full Workflow
```bash
# 1. Validate the return
tax-filler validate --input ./tax_return.md

# 2. Preview what will be filled
tax-filler preview --input ./tax_return.md

# 3. Fill the forms
tax-filler fill --input ./tax_return.md
```

## How It Works

### SSN Handling
Your markdown file has masked SSNs (`***-**-1234`). When filling, the tool prompts you interactively:

```
🔒 SSN Entry Required (never saved to disk)
Enter full SSN for John Doe (***-**-1234): ___-__-____
Enter full SSN for Jane Doe (***-**-5678): ___-__-____
```

SSNs are held in memory only during the filling session and never written to any file.

### Form Filling Order
The tool fills forms in dependency order:
1. Personal information
2. Supporting forms (8949, Schedule C, etc.)
3. Summary schedules (Schedule D, Schedule 1, etc.)
4. Main Form 1040

### Auto-Calculated Fields
FreeFileFillableForms.com auto-calculates some fields (like Line 9 totals). The tool:
1. Skips entering values for auto-calculated fields
2. Reads the auto-calculated value from the page
3. Compares it with the expected value from your markdown
4. Warns you if there's a mismatch

### Verification
After filling each form, the tool reads back all values and compares them with your markdown:

```
✅ Form 1040: 42 fields filled, 3 auto-calculated verified
✅ Schedule D: 12 fields filled
⚠️  Schedule D Line 21: Expected 2500.00, FFFF calculated 2500.00 ✓

Summary:
├── 54 fields filled successfully
├── 3 auto-calculated fields verified ✓
├── 0 mismatches
└── 0 errors

⚠️  Review your return in the browser before submitting.
```

## Field Mappings

The tool uses JSON mapping files to map tax return fields to FFFF page elements:

→ [Form 1040 Mappings](./field-mappings/form-1040-fields.json)

These mappings are updated annually when FFFF updates their site for the new tax year.

## Licensing

| Tier | Forms Supported | Price |
|------|----------------|-------|
| Free | Form 1040 only | $0 |
| Paid | All forms and schedules | $19.99/year |

```bash
# Activate your license
tax-filler activate --key YOUR_LICENSE_KEY
```

## Troubleshooting

### Common Issues

**FFFF site not loading**: Make sure you're using a supported browser (Chrome/Firefox) and have cookies enabled.

**Login issues**: The tool waits for you to log in manually. If you can't create an account, try disabling browser extensions.

**Field not found**: FFFF may have updated their page. Check for tool updates (`npm update -g aitaxprep`) or report the issue.

**Value mismatch**: If the tool reports a mismatch between expected and actual values, review the calculation in your `tax_return.md` and the FFFF form instructions.
