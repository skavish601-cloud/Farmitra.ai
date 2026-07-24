# Skill: GitHub

## When to Use
Managing issues, PRs, labels, milestones, and CI/CD workflows.

## Purpose
Keep repository operations consistent with `CONTRIBUTING.md` and `CLAUDE.md`.

## How to Apply
1. Use the correct issue template (bug/feature/discussion) for the request type
2. Branch naming: `<type>/<short-description>` (e.g. `feature/pest-scan-upload`)
3. Commit messages follow Conventional Commits (`feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`)
4. PRs link their issue, fill out the template fully, and pass all required CI checks (lint, typecheck, test, build, doc checks) before requesting review
5. Squash-merge with a clean Conventional Commit message; delete the branch after merge

## Output Format
Well-labeled issues, template-complete PRs, and green CI.

## Anti-patterns to Avoid
- PRs without a linked issue for non-trivial changes
- Force-pushing over review history mid-review
- Merging with failing or skipped required checks
