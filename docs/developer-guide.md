# Developer Guide

## Getting Started

```bash
git clone https://github.com/skavish601-cloud/Farmitra.ai.git
cd Farmitra.ai
npm install
cp .env.example .env.local   # see docs/environment-variables.md
npm run dev
```

## Before You Start Coding

1. Read `CLAUDE.md` â€” coding standards, architecture rules, checklists
2. Check `.claude/agents/` for the agent whose role matches your task, and read its workflow
3. Check `.claude/skills/` for the relevant reusable skill(s)
4. Check `docs/architecture/` and `docs/database/schema.md` for existing patterns before introducing new ones

## Day-to-Day Workflow

1. Pick up/create an issue using the right template
2. Branch: `<type>/<short-description>` from `main`
3. Implement with tests and docs in the same change
4. Run locally: `npm run lint && npm run typecheck && npm run test && npm run build`
5. Open a PR using the template; link the issue
6. Address review feedback; keep CI green
7. Squash-merge with a Conventional Commit message

Full detail: `CONTRIBUTING.md`, `.claude/rules/git-and-commit-rules.md`, `docs/workflow-guide.md`.

## Working with Claude Code on This Repo

- `.claude/memory/` gives Claude persistent context on the product, stack, and schema â€” read it first in a new session
- `.claude/prompts/` has ready-made prompt templates for feature work, bug fixes, and refactors
- Reference a specific agent explicitly when you want its workflow followed (e.g. "acting as the Supabase Engineer agent, add a migration for...")

## Common Tasks

| Task | Start here |
|---|---|
| Add a UI feature | `.claude/agents/frontend-engineer.md`, `docs/frontend/components.md` |
| Add/change a table | `.claude/agents/supabase-engineer.md`, `docs/database/schema.md` |
| Add an AI-powered feature | `.claude/agents/ai-engineer.md`, `docs/prompt-library.md` |
| Fix a bug | `.claude/skills/debugging.md`, `.claude/prompts/bug-fix.md` |
| Refactor | `.claude/skills/refactoring.md`, `.claude/prompts/refactor.md` |
