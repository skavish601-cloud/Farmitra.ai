# Skill: Code Review

## When to Use
Reviewing any pull request, primarily by the Reviewer agent but applicable to any contributor.

## Purpose
Catch correctness, architecture, security, and quality issues before merge, using the Review Checklist in `CLAUDE.md`.

## How to Apply
1. Confirm CI is green before substantive review
2. Confirm the PR matches its linked issue's scope — flag unrelated drive-by changes
3. Check naming conventions, architecture rules (data flow, logic placement), and coding standards
4. Check tests, docs, and (where relevant) RLS/security, performance, and accessibility considerations
5. Distinguish blocking feedback from suggestions clearly
6. Escalate to a specialized agent (Security Engineer, Performance Engineer) for anything outside reviewer confidence

## Output Format
Inline comments plus a summary review: approve, or request changes with specific, actionable feedback.

## Anti-patterns to Avoid
- Rubber-stamping without reading the diff
- Vague feedback ("this could be better") without a concrete suggestion
- Blocking on personal style preference not covered by documented standards
