# Prompt Template: Bug Fix

```
Reproduce <bug> described in issue #<n>.

Identify root cause before patching — don't just patch the symptom.
Add a regression test that fails before the fix and passes after.
Note the root cause in the PR description.
```

Use for: any reported defect. Pairs with the Debugging skill (`.claude/skills/debugging.md`).
