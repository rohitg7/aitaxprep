---
layout: default
title: AI Tax Prep — AI-First Tax Filing
---

# AI Tax Prep

> ⚠️ **DISCLAIMER**: This project, including all specifications, instructions, and tools, is **developed entirely by AI** and has **not been reviewed, verified, or endorsed by any CPA, tax professional, the IRS, or any other authority**. This is not tax advice. All content may contain errors. **You use this project entirely at your own risk.** You are solely responsible for reviewing and verifying your tax return before filing. Consult a qualified tax professional for your specific situation.

**File your federal taxes for free using AI tools you already have.**

AI Tax Prep is an open specification that lets AI tools (GitHub Copilot, Claude Code, ChatGPT, Cursor, etc.) prepare and file your federal tax return through [IRS Free File Fillable Forms](https://www.freefilefillableforms.com/).

## For AI Tools — Direct Links

If you're an AI agent, go directly to your instructions:
- **Step 1**: [Document Conversion Instructions](./step-1-document-conversion/for-ai-tools)
- **Step 2**: [Tax Return Generation Instructions](./step-2-tax-return/for-ai-tools)

## How It Works

```
  📁 Your Documents     →     🤖 AI Tool (Step 1)     →     🤖 AI Tool (Step 2)     →     🎭 Playwright (Step 3)
  W-2s, 1099s, etc.          Convert to Markdown           Generate Tax Return           Fill FFFF & E-File
```

### Three Simple Steps

| Step | What Happens | Who Does It | Cost |
|------|-------------|-------------|------|
| **1. Document → Markdown** | Convert your tax documents (W-2, 1099, etc.) into structured markdown files | Your AI tool | Free |
| **2. Markdown → Tax Return** | AI analyzes all documents and creates a complete tax return in markdown | Your AI tool | Free |
| **3. Tax Return → E-File** | Playwright script reads your tax return and fills FreeFileFillableForms.com | `aitaxprep` CLI | Freemium |

### What You Need

- Tax documents (PDFs, images, CSVs — any format)
- An AI coding tool (GitHub Copilot, Claude Code, Cursor, ChatGPT, etc.)
- Node.js 18+ (for the form filler)
- An account on [FreeFileFillableForms.com](https://www.freefilefillableforms.com/)

## Quick Start

### Step 1: Convert Your Documents

Point your AI tool to this page and say:

> "Read the instructions at https://rohitg7.github.io/aitaxprep/step-1-document-conversion/ and convert all tax documents in my `~/taxes/2025/documents/` folder to structured markdown."

Your AI will create one `.md` file per document in `~/taxes/2025/docs_md/`.

→ [Step 1: Document Conversion Guide](./step-1-document-conversion/)

### Step 2: Generate Your Tax Return

Then tell your AI:

> "Read the instructions at https://rohitg7.github.io/aitaxprep/step-2-tax-return/ and create my federal tax return from the markdown documents in `~/taxes/2025/docs_md/`."

Your AI will produce `tax_return.md` — a complete, line-by-line tax return.

→ [Step 2: Tax Return Generation Guide](./step-2-tax-return/)

### Step 3: Fill & E-File

```bash
npm install -g aitaxprep
tax-filler fill --input ~/taxes/2025/tax_return.md
```

The tool opens a browser, fills all forms on FreeFileFillableForms.com, and pauses for you to review before submitting.

→ [Step 3: Form Filling Guide](./step-3-form-filling/)

## Scope & Limitations

- **Federal taxes only** — FreeFileFillableForms.com does not support state returns
- **Supported forms**: All forms available on FFFF (1040, Schedules A–F, 8949, 8889, 8863, and more) — [see full list](./reference/supported-forms.md)
- **Not tax advice** — This tool assists with form preparation. Consult a tax professional for complex situations.
- **Human-in-the-loop** — The Playwright tool never auto-submits. You always review and submit manually.

## Security

- **SSNs are masked** in all markdown files (`***-**-1234`)
- **Full SSNs prompted at runtime** only when the Playwright filler needs them
- **No data leaves your machine** — everything runs locally
- **No accounts or signups** — just specs and a CLI tool

## Disclaimer

> ⚠️ **This project is developed entirely by AI.** All specifications, tax rules, form instructions, and tools are AI-generated and have **not been reviewed or verified by any CPA, tax professional, the IRS, or any other authority**. This is not tax advice. All content may contain errors, omissions, or inaccuracies. You use this project entirely at your own risk. You are solely responsible for the accuracy of your tax return. Consult a qualified tax professional for your specific situation. By using this project, you acknowledge and accept these terms.

## Navigation

### For Humans
- [Getting Started](./getting-started/)
- [Step 1: Document Conversion](./step-1-document-conversion/)
- [Step 2: Tax Return Generation](./step-2-tax-return/)
- [Step 3: Form Filling](./step-3-form-filling/)
- [Reference](./reference/)

### For AI Tools
- [Step 1: Document Conversion — AI Instructions](./step-1-document-conversion/for-ai-tools)
- [Step 2: Tax Return Generation — AI Instructions](./step-2-tax-return/for-ai-tools)
