# CLAUDE.md — FarmMitra AI Project Memory

This file is the persistent memory Claude (and any contributor) should read before working in this repository. It defines how we build FarmMitra AI: standards, architecture rules, naming conventions, and the checklists every change should pass before merging.

---

## 1. Project Summary

FarmMitra AI is an AI-powered agriculture assistant for Indian farmers, built as a **Next.js web app** on a **Supabase** backend. Core domains: fields/crops, weather advisories, pest/disease detection, market prices, government scheme eligibility, an AI chat assistant, notifications, and reports. All farmer-facing content is bilingual (Hindi / English), with Hinglish input support and BHASHINI planned for further languages.

Full stack: Next.js, React, TypeScript, Tailwind CSS, shadcn/ui · Supabase (Auth, Postgres, Storage, Edge Functions, Realtime) · Claude / OpenAI / Gemini / BHASHINI for AI · Replit + Vercel for deployment · Figma for design.

---

## 2. Coding Standards

- **TypeScript strict mode always.** No `any` unless justified with a comment explaining why; prefer `unknown` + narrowing.
- **No placeholder code** ("TODO: implement later", stub functions returning fake data) unless explicitly requested — ship working code or clearly mark experimental code as such in a PR description, not silently in the codebase.
- **Functional React components only**, with hooks. No class components.
- **Server Components by default** in the Next.js App Router; add `"use client"` only when interactivity, browser APIs, or hooks require it.
- **Co-locate** component styles, tests, and stories with the component, not in far-away parallel trees.
- **No inline styles** — use Tailwind utility classes; use `cn()` (clsx + tailwind-merge) for conditional classes.
- **Errors are handled, not swallowed.** Every Supabase call checks `error` before using `data`. User-facing errors get a bilingual, farmer-readable message — never a raw stack trace or Postgres error string.
- **All Supabase access goes through `lib/supabase/`** — no ad hoc client instantiation in components.
- **Environment variables** are validated at startup (e.g. via a small schema in `lib/env.ts`); never accessed via bare `process.env.X` scattered through the app.

## 3. Architecture Rules

- **Data flow:** UI components → hooks (`hooks/`) → `lib/` service functions → Supabase client / AI provider client. Components never call `fetch` or the Supabase client directly.
- **RLS is the source of truth for authorization.** Application code must not attempt to replicate authorization logic that the database already enforces — but every new table must ship with RLS enabled and policies reviewed (see Security Checklist).
- **AI provider calls are abstracted** behind a single interface in `lib/ai/` so Claude, OpenAI, Gemini, or BHASHINI can be swapped per use case without touching call sites.
- **Bilingual content uses paired columns** (`field_hi` / `field_en`) at the database level, not runtime translation, for anything stored (schemes, crops, pest names). UI copy/strings use a lightweight i18n dictionary in `lib/i18n/`.
- **Realtime is opt-in per feature** (e.g. notifications) — don't subscribe to Supabase Realtime channels that aren't actively rendered.
- **Edge Functions** are used for anything requiring a secret AI provider key, webhook handling, or scheduled jobs (e.g. daily market price ingestion) — never call provider APIs with secret keys from client code.

## 4. Naming Conventions

| Item | Convention | Example |
|---|---|---|
| Components | PascalCase, one per file | `WeatherCard.tsx` |
| Hooks | camelCase, `use` prefix | `useFieldData.ts` |
| Lib/service functions | camelCase, verb-first | `getMarketPrices()` |
| Types/interfaces | PascalCase | `FieldHealthStatus` |
| Supabase tables/columns | snake_case | `pest_scans`, `confidence_pct` |
| Bilingual columns | `<field>_hi` / `<field>_en` | `name_hi`, `name_en` |
| Route segments (App Router) | kebab-case | `app/crop-advisory/page.tsx` |
| Env vars | `SCREAMING_SNAKE_CASE`, prefixed `NEXT_PUBLIC_` only if client-safe | `NEXT_PUBLIC_SUPABASE_URL` |
| Branches | `<stage-or-type>/<short-description>` | `feature/pest-scan-upload` |
| Commits | [Conventional Commits](https://www.conventionalcommits.org/) | `feat(weather): add irrigation advisory card` |

## 5. Documentation Standards

- Every new feature ships with a short doc in `docs/` (architecture, API, or component doc as appropriate) in the same PR — not "documentation debt" for later.
- Every exported function/component has a one-line JSDoc summary; complex logic gets inline comments explaining *why*, not *what*.
- Database schema changes are documented in `docs/database/` alongside the migration.
- Breaking changes are recorded in `CHANGELOG.md` under `Unreleased` as part of the same PR.

## 6. Development Workflow

1. Pick up or create an issue using the appropriate template (`bug`, `feature`, `discussion`).
2. Branch from `main` using the naming convention above.
3. Implement with tests and docs in the same change — no "add tests later" PRs for core logic.
4. Run the full local check before opening a PR: `npm run lint && npm run typecheck && npm run test && npm run build`.
5. Open a PR using the PR template; link the issue.
6. Address review feedback; CI must be green (lint, typecheck, test, build, doc checks).
7. Squash-merge with a Conventional Commit message; delete the branch.
8. Update `ROADMAP.md`/`CHANGELOG.md` if the change affects them.

---

## 7. Checklists

### Review Checklist
- [ ] Change matches the linked issue's scope (no unrelated drive-by changes)
- [ ] No `any`, no commented-out code, no leftover `console.log`
- [ ] Errors handled and surfaced with bilingual, farmer-appropriate messaging
- [ ] New/changed Supabase tables have RLS enabled and policies reviewed
- [ ] Naming conventions followed
- [ ] Docs updated in the same PR

### Testing Checklist
- [ ] Unit tests for new `lib/` functions and hooks
- [ ] Component tests for interactive UI (forms, chat, dashboards)
- [ ] Edge cases covered: empty state, loading state, error state, offline/slow network
- [ ] RLS policies tested (a user cannot read/write another user's rows)
- [ ] AI provider calls are mocked in tests — no live API calls in CI

### Security Checklist
- [ ] RLS enabled on every table; policies scoped to `auth.uid()` where applicable
- [ ] No secret keys (AI provider keys, service role key) referenced from client-side code
- [ ] User input is validated/sanitized before storage or before use in prompts
- [ ] File uploads (pest scan photos, documents) are size/type restricted and stored in access-controlled buckets
- [ ] Auth flows use Supabase Auth session handling, not custom token logic
- [ ] Dependencies checked for known vulnerabilities (`npm audit`) before release

### Performance Checklist
- [ ] Server Components used by default; client bundle size checked for new client components
- [ ] Images use `next/image` with proper sizing
- [ ] Supabase queries select only needed columns; pagination used for lists (market prices, chat history)
- [ ] Realtime subscriptions cleaned up on unmount
- [ ] AI calls show optimistic/loading UI — no blocking spinners over 300ms without feedback

### Accessibility Checklist
- [ ] Semantic HTML and shadcn/ui primitives used over custom divs where possible
- [ ] All interactive elements keyboard-navigable and have visible focus states
- [ ] Color contrast meets WCAG AA, especially for low-literacy/outdoor mobile use
- [ ] Icons paired with text labels (not icon-only) given the low-literacy target audience
- [ ] Forms have associated labels and error messages announced to screen readers
- [ ] Language toggle (Hindi/English/Hinglish) is accessible from every primary screen

---

## 8. Prompt Templates

**Feature implementation:**
> Implement `<feature>` in `<area>`. Follow CLAUDE.md standards. Read the relevant schema in `docs/database/` and existing patterns in `<similar-file>` before writing code. Include tests and update docs in the same change.

**Bug fix:**
> Reproduce `<bug>` described in issue #`<n>`. Identify root cause before patching. Add a regression test that fails before the fix and passes after.

**Refactor:**
> Refactor `<area>` for `<goal, e.g. readability/performance>` without changing external behavior. Confirm existing tests still pass; add tests first if coverage is missing.

**AI-provider prompt (in-app, for the chat assistant):**
> You are FarmMitra, a helpful agricultural assistant for Indian farmers. Respond in the farmer's language (Hindi/English/Hinglish, matching their input). Be concise, practical, and cite the source when referencing scheme rules or prices. Never invent scheme benefit amounts or prices — say you're not sure rather than guess.

---

## 9. Where to Look Next

- Agents: `.claude/agents/`
- Skills: `.claude/skills/`
- Additional rules: `.claude/rules/`
- Architecture docs: `docs/architecture/`
- Database docs: `docs/database/`
