# Folder Structure

```
.claude/              AI project memory
  agents/              15 specialized agent definitions
  skills/              18 reusable skills
  rules/               Enforced coding/architecture/naming/doc/git rules
  memory/              Product context, tech stack, schema snapshot, decisions log
  prompts/             Reusable prompt templates (implementation, bug fix, AI system prompts)
  checklists/           Review, testing, security, performance, accessibility checklists
  commands/             (reserved for custom Claude Code slash commands)
  templates/            (reserved for additional reusable templates)

.github/
  ISSUE_TEMPLATE/       Bug, feature, and discussion routing templates
  workflows/            CI/CD: lint, typecheck, test, build, deploy, docs-check
  PULL_REQUEST_TEMPLATE.md
  labels.yml

docs/
  architecture/         System design, folder structure, ADRs
  database/              Schema, RLS policy documentation
  api/                   Route Handler / Edge Function reference
  frontend/               Component conventions
  backend/                (reserved for backend-specific deep dives)
  deployment.md
  environment-variables.md
  developer-guide.md
  prompt-library.md
  agent-library.md
  workflow-guide.md

app/                    Next.js App Router pages/layouts/route handlers
components/             Reusable UI components (shadcn/ui-based)
hooks/                  Custom React hooks
lib/                    Shared utilities, Supabase client, AI provider clients, i18n
  supabase/              Supabase client setup (single source of truth for DB access)
  ai/                    Provider-abstracted AI client
  i18n/                  UI string dictionary
types/                  Shared TypeScript types, including generated Supabase types
public/                 Static assets
scripts/                Build, seed, and maintenance scripts
tests/                  Unit, integration, and e2e tests
```

## Notes

- `components/`, `hooks/`, `lib/`, and `types/` are top-level (not under `src/`) per this repo's convention â€” keep new code consistent with that.
- Anything under `.claude/` is documentation/configuration for AI-assisted development, not runtime code.
