# Skill: Next.js

## When to Use
Any page, layout, route handler, or App Router work.

## Purpose
Use the App Router correctly and efficiently.

## How to Apply
1. Server Components by default; add `"use client"` only when interactivity, browser APIs, or hooks require it
2. Route segments use kebab-case (`app/crop-advisory/page.tsx`)
3. Data fetching happens via `lib/` services called from Server Components where possible, not client-side effects
4. Route Handlers for server-only operations that don't fit an Edge Function
5. Use `next/image` for all images with proper sizing

## Output Format
Pages/layouts following the App Router conventions above, with server-first rendering.

## Anti-patterns to Avoid
- Marking a component `"use client"` unnecessarily, bloating the client bundle
- Client-side data fetching where a Server Component would work
- Business logic embedded directly in page components instead of `lib/`
