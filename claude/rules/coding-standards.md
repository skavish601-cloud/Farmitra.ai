# Rule: Coding Standards

These are enforced, not optional â€” PRs violating them should be blocked in review.

1. **TypeScript strict mode always.** No `any` without a comment justifying it; prefer `unknown` + narrowing.
2. **No placeholder code.** No stub functions returning fake data, no `TODO: implement later` left silently in shipped code.
3. **Functional React components only**, with hooks â€” no class components.
4. **Server Components by default** in the App Router; `"use client"` only when interactivity/browser APIs/hooks require it.
5. **Co-locate** styles, tests, and stories with the component.
6. **No inline styles** â€” Tailwind utilities + `cn()` for conditional classes.
7. **Every Supabase call checks `error` before using `data`.** User-facing errors are bilingual and farmer-readable â€” never a raw stack trace or Postgres error string.
8. **All Supabase access goes through `lib/supabase/`** â€” no ad hoc client instantiation in components.
9. **Environment variables validated at startup** (`lib/env.ts`) â€” never bare `process.env.X` scattered through the app.

Source of truth: `CLAUDE.md` Â§2.
