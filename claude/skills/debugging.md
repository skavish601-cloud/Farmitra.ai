# Skill: Debugging

## When to Use
Investigating a reported bug or unexpected behavior.

## Purpose
Find and fix root cause, not symptoms, with a regression test proving the fix.

## How to Apply
1. Reproduce the bug reliably before touching code — if you can't reproduce it, gather more information first
2. Narrow the failure to the smallest reproducible case
3. Check recent changes (`git log`, `git blame`) to the affected area for likely causes
4. Form a hypothesis, verify it (logging, breakpoints, targeted tests), don't guess-and-check in production code
5. Write a failing regression test that captures the bug
6. Fix the root cause; confirm the regression test now passes and the full suite is still green
7. Note the root cause in the PR description, not just the fix

## Output Format
A PR with: root cause explanation, the fix, and a regression test.

## Anti-patterns to Avoid
- Patching symptoms (e.g. adding a null check) without understanding why the null occurred
- Fixing without a regression test
- Debugging directly against production data/systems
