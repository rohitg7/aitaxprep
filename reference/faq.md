# FAQ

## General

### Is this free?
Yes! The tax understanding tool — including document conversion, tax breakdown generation, and the interactive HTML with data lineage — is completely free. The specifications and AI instructions are open source. The optional Playwright form-filler CLI (Step 3) has a free tier (Form 1040 only) and a paid tier ($19.99/year for all forms), but it is not required.

### Is this tax advice?
No. AI Tax Prep is an **educational and informational tool** that helps you understand how your federal taxes work. It generates a tax breakdown showing where every number comes from, but it does not provide tax advice, does not guarantee accuracy, and should not be relied upon for filing decisions. You **must** consult a qualified tax professional before making any tax filing decisions.

### What is the interactive HTML?
The interactive HTML (`tax_return.html`) is the key output of AI Tax Prep. It's a self-contained HTML file where every number is clickable. Click any value to see:
- **Source**: Which document the data came from (e.g., "W-2 from Acme Corp, Box 1")
- **Calculation**: How the number was derived (e.g., "$86,914 = wages + interest + dividends + capital gains")
- **IRS Rule**: The specific IRS instruction or publication that governs that line item

Values are color-coded: green for source document values, blue for calculated values, and yellow for IRS-defined values (like the standard deduction). It's full data lineage for your taxes.

### Which AI tools work with this?
Any AI tool that can read files, follow web instructions, and create files. This includes GitHub Copilot, Claude Code, Cursor, ChatGPT (with file upload), and many others.

### Do I need to be technical?
You need basic familiarity with:
- Using an AI coding tool (giving it prompts)
- Opening an HTML file in a browser
- Reviewing a markdown file

### What tax forms are supported?
All standard federal forms — Form 1040, Schedules A–F, Form 8949, Form 8889, Form 8863, and more. See the [supported forms list](./supported-forms.md).

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
Absolutely — that's the primary use case! Steps 1 and 2 (document conversion and tax breakdown generation) produce a complete analysis with the interactive HTML file. The Playwright form-filler (Step 3) is entirely optional and only needed if you want to auto-fill FreeFileFillableForms.com.

### What happens if FreeFileFillableForms.com changes their website?
The field mapping JSON files would need to be updated. We maintain these annually. If a field fails to fill, the tool logs it and continues, reporting all failures at the end.
