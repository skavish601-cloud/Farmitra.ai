# Skill: Performance

## When to Use
Any change adding a client component, a Supabase query, an image, or an AI call.

## Purpose
Fast, usable experience on mid-range Android devices and slower mobile networks — the realistic target environment.

## How to Apply
1. Default to Server Components; justify any new client component
2. Scope Supabase queries to needed columns; paginate lists (market prices, chat history)
3. Use `next/image` with correct sizing; compress uploads (pest scan photos) before storage
4. Clean up Realtime subscriptions on unmount
5. Show loading feedback for AI calls rather than blocking silently; consider streaming responses

## Output Format
Changes that don't regress bundle size, query cost, or perceived latency, verified where possible with metrics.

## Anti-patterns to Avoid
- `select *` on Supabase queries
- Unbounded lists without pagination
- Blocking spinners over 300ms with no feedback
