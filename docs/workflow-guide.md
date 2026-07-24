# Workflow Guide

End-to-end view of how work moves through this repository, tying together the Planner â†’ implementation agents â†’ Reviewer â†’ Release Manager pipeline.

## 1. Intake

- Idea/bug arrives via a GitHub issue (bug/feature template) or Discussion
- **Planner** breaks it into scoped tasks, assigns owning agent(s), notes dependencies

## 2. Design (if needed)

- **Architect** defines data flow/placement for anything non-trivial; writes an ADR note in `docs/architecture/`
- **UI Designer** produces Figma specs for UI-facing work
- **Supabase Engineer** designs schema changes if data model is affected

## 3. Implementation

- **Frontend / Backend / Supabase / AI Engineer** implement per their agent definitions, following `.claude/rules/` and the relevant `.claude/skills/`
- Tests and docs are written in the same change, not deferred (**Testing Engineer**, **Documentation Engineer** support as needed)

## 4. Review

- **Reviewer** walks the Review Checklist; escalates to **Security Engineer** / **Performance Engineer** for domain-specific concerns
- CI (lint, typecheck, test, build, docs-check) must be green

## 5. Merge & Release

- Squash-merge with a Conventional Commit message
- **Release Manager** periodically finalizes `CHANGELOG.md`, tags releases, coordinates Vercel/Replit deployment
- **Refactoring Engineer** picks up technical debt flagged along the way, in separate PRs

## Diagram

```
Issue/Discussion
      â”‚
      â–¼
   Planner â”€â”€â–º scoped tasks
      â”‚
      â–¼
Architect / UI Designer / Supabase Engineer  (design, as needed)
      â”‚
      â–¼
Frontend / Backend / Supabase / AI Engineer  (implementation + tests + docs)
      â”‚
      â–¼
   Reviewer  â”€â”€â–º Security/Performance Engineer (escalation, as needed)
      â”‚
      â–¼
   Merge to main
      â”‚
      â–¼
Release Manager  â”€â”€â–º CHANGELOG, tag, deploy
```
