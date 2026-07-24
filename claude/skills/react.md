# Skill: React

## When to Use
Building or modifying any component or hook.

## Purpose
Consistent, maintainable React code per `CLAUDE.md`.

## How to Apply
1. Functional components with hooks only — no class components
2. Co-locate styles, tests, and stories with the component
3. Extract shared logic into custom hooks (`hooks/`), named with a `use` prefix
4. Explicit loading/empty/error states for anything async
5. No inline styles — Tailwind utilities via `cn()` for conditional classes

## Output Format
Small, composable components with clear prop types and co-located tests.

## Anti-patterns to Avoid
- Prop drilling more than 2 levels — lift state or use context/hooks instead
- Components that both fetch data and render complex UI — split concerns
- Uncontrolled side effects without cleanup (subscriptions, timers)
