# Changelog

All notable changes to the AI Tax Prep specification will be documented here.

## [1.0.0] — 2026-03-23

### Added
- Initial specification release
- Document conversion schemas: W-2, 1099-INT, 1099-DIV, 1099-B, 1099-NEC, 1098, Charitable, Generic
- Tax return markdown schema v1.0
- Form 1040 AI-optimized instructions
- Validation rules (cross-form, mathematical, business logic)
- IRS source validation requirements (mandatory cross-check with official IRS publications)
- Simple W-2 return end-to-end example
- Playwright form filler specification (Step 3)
- Supported forms reference

### Scope
- Federal taxes only (FreeFileFillableForms.com)
- Tax year 2025 (filing in 2026)

## Schema Versioning

- **Major version** (1.x → 2.x): Breaking changes to field names, table structure, or metadata format
- **Minor version** (1.0 → 1.1): New optional fields, additional forms, non-breaking additions
- The `schema_version` HTML comment in each file tracks which version it conforms to
- AI tools should check `schema_version` and warn if using an outdated version
