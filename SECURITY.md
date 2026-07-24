# Security Policy

FarmMitra AI handles personal data for real farmers (profiles, location, field data, photos, conversations) and integrates with third-party AI providers and Supabase. We take security seriously and appreciate responsible disclosure.

## Reporting a Vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.**

Instead, report privately by opening a [GitHub Security Advisory](https://github.com/skavish601-cloud/Farmitra.ai/security/advisories/new) on this repository (Security tab → "Report a vulnerability"). This creates a private discussion visible only to maintainers until it's resolved.

When reporting, please include:
- A description of the vulnerability and its potential impact
- Steps to reproduce (proof-of-concept code or requests, if applicable)
- Affected version/commit
- Any suggested mitigation, if you have one

## What to Expect

- **Acknowledgment:** within 3 business days
- **Initial assessment:** within 7 business days, including severity and expected timeline
- **Resolution:** timeline depends on severity; critical issues (auth bypass, RLS bypass, data exposure) are prioritized immediately
- We will credit reporters (with permission) once a fix ships, unless you prefer to remain anonymous

## Scope

In scope:
- This repository's application code (frontend, Edge Functions, scripts)
- Supabase configuration as defined in this repo's migrations (RLS policies, schema, storage bucket policies)
- Authentication and session handling

Out of scope:
- Third-party AI provider infrastructure (Claude, OpenAI, Gemini, BHASHINI) — report to the respective provider
- Social engineering, physical attacks, or denial-of-service testing against production infrastructure
- Issues requiring physical access to a farmer's device

## Supported Versions

This project is pre-1.0 and evolving rapidly. Security fixes are applied to the `main` branch and the latest deployed release; older commits are not separately patched.

## Security Practices in This Repo

- Row Level Security (RLS) is required on every Supabase table (see `CLAUDE.md` → Security Checklist)
- Secret keys (Supabase service role key, AI provider keys) are never used client-side and are managed via environment variables / Vercel-Supabase secrets, never committed
- Dependencies are audited (`npm audit`) as part of CI (see `.github/workflows`)
- File uploads (e.g. pest scan photos) are restricted by type/size and stored in access-controlled Storage buckets
- User data collection follows data-minimization principles in line with India's DPDP Act — see `docs/` for the data handling policy once published

## Data Sensitivity Note

Farmer data (location, phone number, field boundaries, photos) is personal and sometimes sensitive. Any change touching data collection, storage, or sharing (including new AI provider integrations that send farmer data externally) should be flagged in the PR description and reviewed with privacy in mind, not just functionality.
