# Architecture Overview

## System Diagram (conceptual)

```
Farmer (browser/mobile)
        â”‚
        â–¼
   Next.js App (Vercel)
   â”œâ”€â”€ Server Components  â”€â”€â–º lib/ services â”€â”€â–º Supabase (Postgres, Auth, Storage, Realtime)
   â”œâ”€â”€ Client Components  â”€â”€â–º hooks/ â”€â”€â–º lib/ services
   â””â”€â”€ Route Handlers     â”€â”€â–º lib/ services â”€â”€â–º Supabase / AI providers (via Edge Functions)

   Supabase Edge Functions
   â”œâ”€â”€ AI provider calls (Claude / OpenAI / Gemini / BHASHINI) â€” secret keys live here only
   â”œâ”€â”€ Scheduled jobs (e.g. market price ingestion)
   â””â”€â”€ Webhooks
```

## Layers

| Layer | Responsibility | Lives in |
|---|---|---|
| UI | Rendering, user interaction | `components/`, `app/` |
| Hooks | Client-side state/data orchestration | `hooks/` |
| Services | Business logic, data access | `lib/` |
| Data | Persistence, auth, storage, realtime | Supabase |
| AI | Provider-abstracted AI calls | `lib/ai/`, Edge Functions |

## Core Rule

UI components never call Supabase or an AI provider directly. Everything flows through `lib/` services, which are the single place that knows how to talk to Supabase and AI providers. This keeps components simple, testable, and swappable, and keeps authorization logic centralized (RLS) rather than duplicated in the client.

## Why This Shape

- **Server Components by default** minimizes client JS shipped to low-end Android devices on slow networks â€” a core constraint for FarmMitra's user base.
- **RLS as the authorization boundary** means even a compromised or buggy client can't read/write data it shouldn't â€” the database enforces it regardless of what the UI does.
- **AI provider abstraction** lets us swap Claude/OpenAI/Gemini/BHASHINI per use case (cost, language support, capability) without rewriting call sites.

See `.claude/rules/architecture-rules.md` for the enforced rules, and `.claude/memory/decisions-log.md` for the history of why key choices were made.
