# Prompt Template: Refactor

```
Refactor <area> for <goal, e.g. readability/performance/consistency>
without changing external behavior.

Confirm existing tests still pass after the change; add characterization
tests first if coverage is missing. Do not bundle feature changes into
this PR.
```

Use for: technical debt cleanup, pattern migrations. Pairs with `.claude/skills/refactoring.md`.
