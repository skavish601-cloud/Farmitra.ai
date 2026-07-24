# Deployment

## Environments

| Environment | Platform | Trigger |
|---|---|---|
| Production | Vercel | Push/merge to `main` (see `.github/workflows/deploy.yml`) |
| Preview/Development | Replit | Manual, or future automated hook (currently disabled in `deploy.yml`) |

## Vercel (Production)

1. Import the GitHub repo into Vercel (one-time setup, done via Vercel's dashboard, not this repo)
2. Configure environment variables in the Vercel project settings â€” see `docs/environment-variables.md`
3. `main` branch is the production branch; every merge triggers a deploy via `.github/workflows/deploy.yml`
4. Required GitHub repo secrets for the workflow: `VERCEL_TOKEN`, `VERCEL_ORG_ID`, `VERCEL_PROJECT_ID` (added under **Settings â†’ Secrets and variables â†’ Actions** on GitHub â€” never committed to the repo or shared in chat/issues)

## Replit (Development / Preview)

Used for fast iteration and sharing in-progress work. Connect the repo in Replit and configure the same environment variables as Vercel for local parity. The automated preview-deploy job in `deploy.yml` is currently disabled (`if: false`) until a deploy hook is configured â€” enable it once that's set up.

## Supabase

Supabase is a managed service â€” there's no "deploy" step for the database itself, but:

- Migrations are applied via `supabase db push` or the Supabase MCP/CLI, not manually through the dashboard, to keep `docs/database/schema.md` and actual state in sync
- Edge Functions are deployed via `supabase functions deploy <name>`
- Never apply a migration directly against production without it existing as a versioned file first

## Rollback

- **App (Vercel):** use Vercel's dashboard to instantly roll back to a previous deployment
- **Database:** Supabase migrations are forward-only by convention here â€” a rollback is a new migration that reverses the change, not a destructive revert. Coordinate with the Supabase Engineer and Release Manager agents before rolling back schema changes with live data.

## Pre-Release Checklist

See `.claude/agents/release-manager.md` for the full release workflow.
