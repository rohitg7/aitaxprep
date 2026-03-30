# Getting Started

## Overview

AI Tax Prep is a specification-first system. Instead of building a monolithic tax app, we provide **structured instructions** that your AI tools follow to prepare your taxes.

### The Philosophy

Traditional tax software asks *you* questions and fills forms. AI Tax Prep flips this:

1. **You** collect your documents into a folder
2. **Your AI tool** reads our specs and converts documents to markdown
3. **Your AI tool** reads our specs and generates a complete tax return
4. **Our CLI tool** reads the tax return and fills the IRS e-filing website

You stay in control. The AI does the heavy lifting. You review everything before filing.

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
- **Node.js 18+** — For the Playwright form filler

### Required Python Package
```bash
pip install 'markitdown[all]'
```
[markitdown](https://github.com/microsoft/markitdown) is Microsoft's trusted document-to-markdown converter. It handles PDFs, images, Excel, CSV, Word, and more.

### Required for E-Filing
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
    └── tax_return.md            # Step 2 output: complete tax return
```

## Workflow

### Step 1: Document Conversion

1. Put all your tax documents in `taxes/2025/documents/`
2. Open your AI tool in the `taxes/2025/` directory
3. Tell it:
   > "Read the document conversion instructions at https://rohitg7.github.io/aitaxprep/step-1-document-conversion/for-ai-tools and convert all files in `./documents/` to structured markdown. Save output to `./docs_md/`."
4. Review the generated markdown files for accuracy

→ [Detailed Step 1 Guide](../step-1-document-conversion/)

### Step 2: Tax Return Generation

1. With the AI tool still open in `taxes/2025/`:
   > "Read the tax return instructions at https://rohitg7.github.io/aitaxprep/step-2-tax-return/for-ai-tools and generate my federal tax return from the documents in `./docs_md/`. Save as `./tax_return.md`."
2. **Review the tax return carefully** — check all numbers against your documents
3. The AI will include a validation report at the bottom

→ [Detailed Step 2 Guide](../step-2-tax-return/)

### Step 3: Fill & E-File

```bash
# Install the form filler
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

→ [Detailed Step 3 Guide](../step-3-form-filling/)

## Security Considerations

### SSN Protection
- All markdown files mask SSNs: `***-**-1234` (only last 4 digits visible)
- Full SSNs are entered interactively at runtime when filling forms
- SSNs are never written to disk in unmasked form

### Data Privacy
- Everything runs on your machine — no data is sent to any server
- The spec website contains only instructions, not your data
- The form filler CLI works offline (except for accessing FreeFileFillableForms.com)

### AI Tool Considerations
- Be aware of your AI tool's data policies — some may send file contents to their servers
- For maximum privacy, use local AI models or tools that process data on-device
- Consider using `.gitignore` or equivalent to prevent accidentally committing tax files

## Disclaimer

⚠️ **AI Tax Prep is not tax advice.** This tool assists with form preparation based on the documents you provide. It does not guarantee accuracy or completeness. You are responsible for reviewing your tax return before filing. Consult a qualified tax professional for complex tax situations.
