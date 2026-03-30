# FAQ

## General

### Is this free?
The specification website and AI tool instructions are completely free and open source. The Playwright form-filler CLI has a free tier (Form 1040 only) and a paid tier ($19.99/year for all forms).

### Is this tax advice?
No. AI Tax Prep is a tool that assists with form preparation. It does not provide tax advice. You are responsible for reviewing your tax return before filing. Consult a qualified tax professional for complex situations.

### Which AI tools work with this?
Any AI tool that can read files, follow web instructions, and create files. This includes GitHub Copilot, Claude Code, Cursor, ChatGPT (with file upload), and many others.

### Do I need to be technical?
You need basic familiarity with:
- Using an AI coding tool (giving it prompts)
- Running a command in a terminal (`npm install`, `tax-filler fill`)
- Reviewing a markdown file

### What tax forms are supported?
All federal forms available on [IRS Free File Fillable Forms](https://www.freefilefillableforms.com/). See the [supported forms list](./supported-forms.md).

## Security

### Are my SSNs safe?
Yes. SSNs are masked (`***-**-1234`) in all markdown files. Full SSNs are only entered interactively at runtime when filling forms, held in memory only, and never written to disk.

### Does my data go to any server?
No. Everything runs on your machine. The spec website contains only instructions, not your data. The form filler works locally (it only connects to FreeFileFillableForms.com to fill forms).

### What about the AI tool?
Be aware of your AI tool's privacy policies. Some AI tools may send file contents to their servers for processing. For maximum privacy, use AI tools that process data locally.

## Technical

### Why markdown and not JSON/XML?
Markdown is:
1. Human-readable — you can review your tax return in any text editor
2. AI-friendly — all AI tools can generate and parse markdown
3. Simple — no complex data structures to debug
4. Versionable — works great with git

### Why Playwright instead of a browser extension?
1. No Chrome Web Store approval needed
2. More reliable (full browser control)
3. AI tools like Claude Code can run it directly
4. Easier to develop, test, and debug
5. Users already have Node.js if they're using AI coding tools

### Can I use this without the Playwright tool?
Yes! Steps 1 and 2 (document conversion and tax return generation) work without it. You can manually enter values from your `tax_return.md` into FreeFileFillableForms.com. The Playwright tool just automates that last step.

### What happens if FreeFileFillableForms.com changes their website?
The field mapping JSON files would need to be updated. We maintain these annually. If a field fails to fill, the tool logs it and continues, reporting all failures at the end.
