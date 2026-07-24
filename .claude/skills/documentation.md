# Skill: Documentation

## When to Use
In the same PR as any feature, schema change, or architecture decision.

## Purpose
Keep `docs/` accurate and useful, per the Documentation Standards in `CLAUDE.md`.

## How to Apply
1. Identify which doc area is affected: `docs/architecture/`, `docs/database/`, `docs/api/`, `docs/frontend/`, `docs/backend/`
2. Write concisely — prefer tables/diagrams over long prose
3. Document *why*, not just *what*, for non-obvious decisions
4. Update `CHANGELOG.md` under `[Unreleased]` for user-facing or breaking changes
5. Never describe planned-but-unbuilt behavior as if it exists — mark it as planned

## Output Format
Short, example-driven docs co-located with the relevant `docs/` subfolder.

## Anti-patterns to Avoid
- Documentation debt ("will document later")
- Exhaustive prose where a table would communicate faster
- Docs that drift from actual code behavior
