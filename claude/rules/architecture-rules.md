# Rule: Architecture Rules

1. **Data flow is fixed:** UI components → hooks (`hooks/`) → `lib/` service functions → Supabase client / AI provider client. Components never call `fetch` or the Supabase client directly.
2. **RLS is the source of truth for authorization.** Application code must not replicate authorization logic the database already enforces. Every new table ships with RLS enabled and reviewed policies.
3. **AI provider calls are abstracted** behind a single interface in `lib/ai/` so Claude, OpenAI, Gemini, or BHASHINI can be swapped per use case without touching call sites.
4. **Bilingual stored content uses paired columns** (`field_hi` / `field_en`), not runtime translation. UI copy uses the `lib/i18n/` dictionary.
5. **Realtime is opt-in per feature** — don't subscribe to channels that aren't actively rendered.
6. **Edge Functions** are required for anything needing a secret AI provider key, webhook handling, or scheduled jobs. Never call provider APIs with secret keys from client code.

Source of truth: `CLAUDE.md` §3. Deviations require an Architect-reviewed decision note in `docs/architecture/`.
