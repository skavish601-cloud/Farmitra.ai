# Rule: Documentation Rules

1. Every new feature ships with a short doc in `docs/` in the **same PR** — not deferred.
2. Every exported function/component has a one-line JSDoc summary; complex logic gets inline comments explaining *why*.
3. Database schema changes are documented in `docs/database/` alongside the migration.
4. Breaking or user-facing changes are recorded in `CHANGELOG.md` under `[Unreleased]` in the same PR.
5. Documentation must never describe planned-but-unbuilt behavior as if it already exists.

Source of truth: `CLAUDE.md` §5.
