# Skill: Refactoring

## When to Use
Improving code structure, readability, or performance without changing external behavior.

## Purpose
Reduce technical debt safely, backed by tests, without bundling in feature changes.

## How to Apply
1. Confirm test coverage exists for the behavior being preserved; add characterization tests first if missing
2. Make the smallest coherent change that achieves the structural goal
3. Run the full test suite before and after — behavior must be identical
4. Update documentation referencing the old structure
5. Keep the refactor in its own PR, separate from any feature work

## Output Format
A PR with no behavior change, verified by passing tests, and a clear description of what structure changed and why.

## Anti-patterns to Avoid
- Refactoring and adding features in the same PR
- Large rewrites without Architect sign-off
- Refactors with no test safety net
