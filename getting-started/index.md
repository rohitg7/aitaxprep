# Getting Started

> ⚠️ **DISCLAIMER**: This project is developed entirely by AI and has not been reviewed or verified by any CPA, tax professional, the IRS, or any other authority. This is **for educational and informational purposes only**. This is not tax advice. You use this project entirely at your own risk. Consult a qualified tax professional before making any tax filing decisions.

## Overview

AI Tax Prep is a specification-first system. Instead of building a monolithic tax app, we provide **structured instructions** that your AI tools follow to analyze your taxes and produce an interactive breakdown with full data lineage.

### The Philosophy

Traditional tax software shows you the final number — what you owe or what your refund is. But it doesn't show you *how* every number was derived.

AI Tax Prep flips this:

1. **You** collect your documents into a folder
2. **Your AI tool** reads our specs and converts documents to markdown
3. **Your AI tool** reads our specs and generates a complete tax breakdown — both a detailed markdown analysis and an **interactive HTML file** where you can click any number and trace it back to the source document, see the calculation, and read the IRS rule that applies

You stay in control. The AI does the heavy lifting. You understand everything before making any filing decisions.

## Prerequisites

### Required
- **Tax documents** — W-2s, 1099s, brokerage statements, etc. (any format: PDF, image, CSV, Excel)
- **An AI coding tool** — Any of these work:
  - [GitHub Copilot](https://github.com/features/copilot) (in VS Code, JetBrains, or CLI)
  - [Claude Code](https://claude.ai) (Anthropic's coding assistant)
  - [Cursor](https://cursor.sh)
  - [ChatGPT](https://chat.openai.com) (with file upload)
  - Any AI tool that can read files, follow instructions, and create files
- **Python 3.10+** — For the markitdown document converter

### Required Python Package
```bash
pip install 'markitdown[all]'
```
[markitdown](https://github.com/microsoft/markitdown) is Microsoft's trusted document-to-markdown converter. It handles PDFs, images, Excel, CSV, Word, and more.

### Optional (for Form Filling — Advanced)
- **Node.js 18+** — For the Playwright form filler (Step 3)
- **FreeFileFillableForms.com account** — Create one at [freefilefillableforms.com](https://www.freefilefillableforms.com/). You need a new account each tax year.

## Folder Structure

We recommend organizing your tax files like this:

```
taxes/
└── 2025/                        # Tax year
    ├── documents/               # Original documents (any format)
    │   ├── w2_acme.pdf
    │   ├── 1099_int_chase.pdf
    │   ├── 1099_div_vanguard.pdf
    │   ├── brokerage_schwab.csv
    │   └── donation_receipts.jpg
    │
    ├── docs_md/                 # Step 1 output: documents as markdown
    │   ├── _index.md
    │   ├── w2_1.md
    │   ├── 1099_int_1.md
    │   ├── 1099_div_1.md
    │   ├── 1099_b_1.md
    │   └── charitable_1.md
    │
    ├── tax_return.md            # Step 2 output: detailed tax breakdown
    └── tax_return.html          # Step 2 output: interactive breakdown with lineage
```

## Workflow

### Step 1: Document Conversion

1. Put all your tax documents in `taxes/2025/documents/`
2. Open your AI tool in the `taxes/2025/` directory
3. Tell it:
   > "Read the document conversion instructions at https://rohitg7.github.io/aitaxprep/step-1-document-conversion/for-ai-tools and convert all files in `./documents/` to structured markdown. Save output to `./docs_md/`."
4. Review the generated markdown files for accuracy

→ [Detailed Step 1 Guide](../step-1-document-conversion/)

### Step 2: Tax Breakdown Generation

1. With the AI tool still open in `taxes/2025/`:
   > "Read the tax breakdown instructions at https://rohitg7.github.io/aitaxprep/step-2-tax-return/for-ai-tools and generate my federal tax breakdown from the documents in `./docs_md/`."
2. Your AI will produce two files:
   - `tax_return.md` — detailed line-by-line tax breakdown
   - `tax_return.html` — interactive HTML with full data lineage
3. **Open `tax_return.html` in your browser** — click any number to trace it back to its source
4. **Review the breakdown carefully** — check all numbers against your documents

→ [Detailed Step 2 Guide](../step-2-tax-return/)

### Optional: Step 3 — Form Filling (Advanced)

For advanced users who want to auto-fill IRS Free File Fillable Forms:

```bash
# Install the form filler (requires Node.js 18+)
npm install -g aitaxprep

# Validate your tax return first
tax-filler validate --input ./tax_return.md

# Fill the forms (opens a browser)
tax-filler fill --input ./tax_return.md
```

The tool will:
1. Parse your tax return markdown
2. Open a browser to FreeFileFillableForms.com
3. Wait for you to log in
4. Fill all form fields automatically
5. Pause so you can review everything
6. You manually click Submit when satisfied

→ [Detailed Step 3 Guide (Optional)](../step-3-form-filling/)

## Security Considerations

### SSN Protection
- All markdown files mask SSNs: `***-**-1234` (only last 4 digits visible)
- SSNs are never written to disk in unmasked form

### Data Privacy
- Everything runs on your machine — no data is sent to any server
- The spec website contains only instructions, not your data

### AI Tool Considerations
- Be aware of your AI tool's data policies — some may send file contents to their servers
- For maximum privacy, use local AI models or tools that process data on-device
- Consider using `.gitignore` or equivalent to prevent accidentally committing tax files

## Disclaimer

⚠️ **AI Tax Prep is for educational and informational purposes only.** This tool helps you understand your taxes based on the documents you provide. It does not guarantee accuracy or completeness. This is not tax advice. You must consult a qualified tax professional before making any tax filing decisions.
