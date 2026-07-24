# Skill: Supabase

## When to Use
Any schema, RLS, Storage, Edge Function, or Realtime work.

## Purpose
Keep the Supabase project (`farmmitra.ai`) consistent, secure, and well-documented.

## How to Apply
1. Every new table gets RLS enabled and policies scoped to `auth.uid()` by default
2. Bilingual content uses paired `_hi`/`_en` columns, not runtime translation, for stored data
3. Write migrations that include RLS policies and indexes together where practical
4. Regenerate TypeScript types (`types/supabase.ts`) after schema changes
5. Storage buckets get explicit access policies — never a public-write bucket for user-uploaded content (e.g. pest scan photos)
6. Use Edge Functions for anything needing a secret key or webhook/scheduled behavior

## Output Format
A migration file, RLS policies, regenerated types, and a `docs/database/` update.

## Anti-patterns to Avoid
- Tables without RLS "for now"
- Runtime translation of stored farmer-facing content instead of paired columns
- Client-side use of the service role key
