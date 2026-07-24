# Environment Variables

Copy `.env.example` to `.env.local` for local development. Never commit `.env.local` or any file containing real secrets.

## Client-safe (exposed to the browser â€” prefix `NEXT_PUBLIC_`)

| Variable | Purpose |
|---|---|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase project API URL |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase anonymous/publishable key (safe for client use â€” RLS enforces real access control) |

## Server-only (never exposed to the browser)

| Variable | Purpose |
|---|---|
| `SUPABASE_SERVICE_ROLE_KEY` | Full-access Supabase key â€” server/Edge Function use only, never in client code |
| `ANTHROPIC_API_KEY` | Claude API access |
| `OPENAI_API_KEY` | OpenAI API access |
| `GEMINI_API_KEY` | Google Gemini API access |
| `BHASHINI_API_KEY` | BHASHINI language services access |

## CI/CD (GitHub Actions repo secrets, not in `.env`)

| Secret | Purpose |
|---|---|
| `VERCEL_TOKEN`, `VERCEL_ORG_ID`, `VERCEL_PROJECT_ID` | Used by `.github/workflows/deploy.yml` |
| `REPLIT_DEPLOY_HOOK_URL` | Used by the (currently disabled) Replit preview deploy job |

## Rules

- All env vars are validated at startup via a schema in `lib/env.ts` (per `.claude/rules/coding-standards.md`) â€” never accessed via bare `process.env.X` scattered through the app
- If a variable doesn't need to reach the browser, it must **not** have the `NEXT_PUBLIC_` prefix
- Add any new variable to `.env.example` (with a placeholder, not a real value) in the same PR that introduces it
