# API Reference

FarmMitra doesn't expose a general public REST API yet (Phase 4 in `ROADMAP.md`). Internally, "API surface" means:

1. **Next.js Route Handlers** (`app/api/**/route.ts`) â€” for server-only operations not requiring a secret key
2. **Supabase Edge Functions** â€” for anything requiring a secret key (AI provider calls), webhook handling, or scheduled jobs
3. **Supabase auto-generated REST/RPC** â€” used directly via the Supabase client from `lib/supabase/` for standard CRUD, governed entirely by RLS

## Conventions

- All Route Handlers and Edge Functions validate input before processing and return typed, consistent error shapes:
  ```ts
  { error: { message: string; code?: string } }
  ```
- No secret keys (AI provider keys, Supabase service role key) are ever referenced in code that ships to the client.
- Endpoints are documented here as they're added, with: purpose, method, auth requirement, request/response shape.

## Endpoint Log

_(To be populated as Route Handlers and Edge Functions are implemented in Stage 7+.)_

| Endpoint | Method | Auth | Purpose |
|---|---|---|---|
| _none yet_ | | | |

## Adding a New Endpoint

1. Decide placement per `.claude/rules/architecture-rules.md` (Route Handler vs. Edge Function vs. direct Supabase call)
2. Implement with input validation and the standard error shape above
3. Add a row to the Endpoint Log in this file in the same PR
4. Add tests per `.claude/checklists/testing-checklist.md`
