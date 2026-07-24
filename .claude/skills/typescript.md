# Skill: TypeScript

## When to Use
All code in this repository — TypeScript strict mode is non-negotiable.

## Purpose
Type safety and clarity per `CLAUDE.md`.

## How to Apply
1. Strict mode always; no `any` without a comment justifying it — prefer `unknown` + narrowing
2. Shared types live in `types/`, including generated Supabase types
3. Types/interfaces use PascalCase (`FieldHealthStatus`)
4. Prefer discriminated unions for state (e.g. `{status: 'loading'} | {status: 'error', message: string} | {status: 'success', data: T}`) over multiple booleans
5. Export types alongside the functions/components that use them when not broadly shared

## Output Format
Fully-typed functions, components, and API contracts with no implicit `any`.

## Anti-patterns to Avoid
- `as` casts to silence type errors instead of fixing the underlying type
- Duplicated type definitions instead of importing from `types/`
- Loosening `tsconfig.json` strictness to work around an error
