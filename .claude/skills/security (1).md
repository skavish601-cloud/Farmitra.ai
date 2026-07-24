# Skill: Security

## When to Use
Any change touching auth, data access, file uploads, or external integrations.

## Purpose
Protect farmer data and system integrity per the Security Checklist in `CLAUDE.md` and `SECURITY.md`.

## How to Apply
1. Every table has RLS enabled and policies scoped to `auth.uid()` where applicable
2. No secret keys (AI provider keys, Supabase service role key) in client-side code
3. Validate/sanitize user input before storage or before use in AI prompts
4. Restrict file uploads by type/size; store in access-controlled buckets
5. Use Supabase Auth session handling — no custom token logic
6. Run `npm audit` and address known vulnerabilities before release

## Output Format
Changes that pass the Security Checklist, with RLS tested against a non-owner user where relevant.

## Anti-patterns to Avoid
- "We'll add RLS later"
- Logging PII or secrets
- Trusting client-supplied data without server-side validation
