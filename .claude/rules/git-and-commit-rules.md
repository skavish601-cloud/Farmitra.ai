# Rule: Git & Commit Rules

1. Branch from `main`: `<type>/<short-description>` (e.g. `feature/pest-scan-upload`, `fix/weather-card-timezone`).
2. Commits follow [Conventional Commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`.
3. Before opening a PR, run: `npm run lint && npm run typecheck && npm run test && npm run build`.
4. PRs link their issue and complete the PR template fully.
5. Don't force-push over review history mid-review — push new commits instead.
6. Squash-merge with a clean Conventional Commit message; delete the branch after merge.
7. Refactors and features are never bundled in the same PR.

Source of truth: `CLAUDE.md` §6, `CONTRIBUTING.md`.
