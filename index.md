---
layout: default
title: AI Tax Prep — Understand Your Federal Taxes with AI
---

# AI Tax Prep

> ⚠️ **DISCLAIMER**: This project, including all specifications, instructions, and tools, is **developed entirely by AI** and has **not been reviewed, verified, or endorsed by any CPA, tax professional, the IRS, or any other authority**. This is **for educational and informational purposes only**. This is not tax advice. All content may contain errors. **You use this project entirely at your own risk.** Consult a qualified tax professional before making any tax filing decisions.

**Understand your federal taxes using AI tools you already have.**

AI Tax Prep is an open specification that lets AI tools (GitHub Copilot, Claude Code, ChatGPT, Cursor, etc.) analyze your tax documents and produce an interactive tax breakdown with full data lineage — so you can see exactly where every number comes from.

## For AI Tools — Direct Links

If you're an AI agent, go directly to your instructions:
- **Step 1**: [Document Conversion Instructions](./step-1-document-conversion/for-ai-tools)
- **Step 2**: [Tax Breakdown Generation Instructions](./step-2-tax-return/for-ai-tools)

## How It Works

```
  📁 Your Documents     →     🤖 AI Tool (Step 1)     →     🤖 AI Tool (Step 2)
  W-2s, 1099s, etc.          Convert to Markdown           Generate Tax Breakdown
                                                              ↓
                                                        📄 tax_return.md (detailed breakdown)
                                                        🌐 tax_return.html (interactive with lineage)
```

### Two Simple Steps

| Step | What Happens | Who Does It |
|------|-------------|-------------|
| **1. Document → Markdown** | Convert your tax documents (W-2, 1099, etc.) into structured markdown files | Your AI tool |
| **2. Markdown → Tax Breakdown** | AI analyzes all documents and generates a complete tax breakdown with an interactive HTML file showing full data lineage | Your AI tool |

### What You Get

- **`tax_return.md`** — Detailed line-by-line tax analysis in readable markdown. Every line item includes the value, its source document, and the IRS rule that applies.
- **`tax_return.html`** — Interactive HTML where every number is clickable. Click any value to see:
  - **Where it came from** — which document, which box (e.g., "W-2 from Acme Corp, Box 1")
  - **How it was calculated** — the full formula and components (e.g., "$86,914.25 = wages + interest + dividends + capital gains")
  - **The IRS rule** — the specific IRS instruction or publication that governs that line

### What You Need

- Tax documents (PDFs, images, CSVs — any format)
- An AI coding tool (GitHub Copilot, Claude Code, Cursor, ChatGPT, etc.)
- Python 3.10+ (for the markitdown document converter)

## Quick Start

### Step 1: Convert Your Documents

Point your AI tool to this page and say:

> "Read the instructions at https://rohitg7.github.io/aitaxprep/step-1-document-conversion/ and convert all tax documents in my `~/taxes/2025/documents/` folder to structured markdown."

Your AI will create one `.md` file per document in `~/taxes/2025/docs_md/`.

→ [Step 1: Document Conversion Guide](./step-1-document-conversion/)

### Step 2: Generate Your Tax Breakdown

Then tell your AI:

> "Read the instructions at https://rohitg7.github.io/aitaxprep/step-2-tax-return/ and generate my federal tax breakdown from the markdown documents in `~/taxes/2025/docs_md/`."

Your AI will produce:
- `tax_return.md` — a detailed, line-by-line tax breakdown
- `tax_return.html` — an interactive HTML file with full data lineage

→ [Step 2: Tax Breakdown Guide](./step-2-tax-return/)

## Optional: Form Filling (Advanced)

For advanced users who want to auto-fill [IRS Free File Fillable Forms](https://www.freefilefillableforms.com/) using the generated tax data:

```bash
npm install -g aitaxprep
tax-filler fill --input ~/taxes/2025/tax_return.md
```

This requires Node.js 18+ and an account on FreeFileFillableForms.com. The tool opens a browser, fills all forms, and pauses for you to review before submitting.

→ [Step 3: Form Filling Guide (Optional)](./step-3-form-filling/)

## Scope & Limitations

- **Federal taxes only** — covers all standard federal forms (1040, Schedules A–F, 8949, 8889, 8863, and more) — [see full list](./reference/supported-forms.md)
- **Educational purpose** — This tool helps you understand your taxes. It is not tax advice.
- **Human review required** — Always review the generated breakdown and consult a tax professional before making any filing decisions.

## Security

- **SSNs are masked** in all markdown files (`***-**-1234`)
- **No data leaves your machine** — everything runs locally
- **No accounts or signups** — just specs and your AI tool

## Disclaimer

> ⚠️ **This project is developed entirely by AI and is for educational and informational purposes only.** All specifications, tax rules, form instructions, and tools are AI-generated and have **not been reviewed or verified by any CPA, tax professional, the IRS, or any other authority**. This is not tax advice. All content may contain errors, omissions, or inaccuracies. You use this project entirely at your own risk. You must consult a qualified tax professional before making any tax filing decisions. By using this project, you acknowledge and accept these terms.

## Navigation

### For Humans
- [Getting Started](./getting-started/)
- [Step 1: Document Conversion](./step-1-document-conversion/)
- [Step 2: Tax Breakdown](./step-2-tax-return/)
- [Step 3: Form Filling (Optional)](./step-3-form-filling/)
- [Reference](./reference/)

### For AI Tools
- [Step 1: Document Conversion — AI Instructions](./step-1-document-conversion/for-ai-tools)
- [Step 2: Tax Breakdown — AI Instructions](./step-2-tax-return/for-ai-tools)
