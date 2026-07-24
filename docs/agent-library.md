# Agent Library

Index of the 15 specialized agents in `.claude/agents/`. Each has full Role / Responsibilities / Inputs / Outputs / Workflow / Best Practices in its own file â€” this is a quick-reference map of when to use which.

| Agent | Use when... |
|---|---|
| [Planner](../.claude/agents/planner.md) | Breaking down a roadmap item or request into scoped tasks |
| [Architect](../.claude/agents/architect.md) | Designing or reviewing system-level structure |
| [Frontend Engineer](../.claude/agents/frontend-engineer.md) | Building UI, pages, or hooks |
| [Backend Engineer](../.claude/agents/backend-engineer.md) | Building Route Handlers, Edge Functions, server logic |
| [Supabase Engineer](../.claude/agents/supabase-engineer.md) | Schema, RLS, migrations, Storage |
| [UI Designer](../.claude/agents/ui-designer.md) | Designing screens/flows in Figma |
| [AI Engineer](../.claude/agents/ai-engineer.md) | Prompt design, provider integration |
| [Testing Engineer](../.claude/agents/testing-engineer.md) | Writing/reviewing test coverage |
| [Security Engineer](../.claude/agents/security-engineer.md) | Reviewing auth, RLS, data handling |
| [Performance Engineer](../.claude/agents/performance-engineer.md) | Reviewing bundle size, queries, latency |
| [Documentation Engineer](../.claude/agents/documentation-engineer.md) | Maintaining `docs/` |
| [GitHub Engineer](../.claude/agents/github-engineer.md) | Templates, labels, CI workflows |
| [Reviewer](../.claude/agents/reviewer.md) | Final PR review before merge |
| [Refactoring Engineer](../.claude/agents/refactoring-engineer.md) | Structural cleanup without behavior change |
| [Release Manager](../.claude/agents/release-manager.md) | Coordinating a release/deployment |

## Invoking an Agent

When working with Claude Code on this repo, reference the agent explicitly for focused behavior, e.g.:

> "Acting as the Supabase Engineer agent (see `.claude/agents/supabase-engineer.md`), add a migration for a new `irrigation_logs` table with RLS."
