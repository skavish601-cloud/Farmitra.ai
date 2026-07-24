# Skill: Testing

## When to Use
Alongside every implementation — tests are part of the change, not a follow-up.

## Purpose
Ensure correctness and prevent regressions, per the Testing Checklist in `CLAUDE.md`.

## How to Apply
1. Unit test `lib/` functions and hooks in isolation
2. Component test interactive UI (forms, chat, dashboards), covering loading/empty/error states
3. Test RLS policies with a non-owner user to confirm access is denied where expected
4. Mock AI provider calls — never call live AI APIs in CI
5. Add e2e coverage for critical flows: auth, chat, disease detection upload, scheme eligibility
6. Run `npm run test` locally before opening a PR

## Output Format
Test files co-located with or in `tests/`, covering the behaviors listed above.

## Anti-patterns to Avoid
- Testing implementation details instead of behavior
- Skipping RLS negative tests
- Leaving flaky tests skipped indefinitely instead of fixing or removing them
