# ðŸŒ¾ FarmMitra AI

**An AI-powered agriculture assistant and organization for Indian farmers.**

FarmMitra ("Farm + Mitra" â€” "friend of the farm") helps farmers manage their fields, get weather-linked advisories, diagnose crop pests, track mandi (market) prices, check government scheme eligibility, and chat with an AI assistant â€” in Hindi, English, or Hinglish ,many regional language 22+.

This repository follows the **Everything Claude Code** development philosophy: an AI-first project layout with reusable agents, skills, project memory, and rules that let Claude (and human contributors) work on this codebase consistently and safely.

---

## Product Overview

| | |
|---|---|
| **Languages** | Hindi, English, Hinglish (future languages via BHASHINI or sarvam Ai) |
| **Frontend** | Next.js, React, TypeScript, Tailwind CSS, shadcn/ui |
| **Backend** | Supabase (Auth, Database, Storage, Edge Functions, Realtime) |
| **AI** | Claude, OpenAI, Gemini, BHASHINI, Cursor ,Open design ,Claude code |
| **Deployment** | Replit, Vercel |
| **Design** | Figma |


## 🎨 Design

**Figma UI/UX**
- Design File: https://www.figma.com/make/zKWto6ta7dwWlYZmpHiIKH/frammitra.ai?t=MsxfWYbHoCiQCoiC-1
- Prototype: https://www.figma.com/make/zKWto6ta7dwWlYZmpHiIKH/frammitra.ai?t=MsxfWYbHoCiQCoiC-1


> Keep the Figma file updated. All UI changes should be made in Figma before implementation.
## Core Features

- **Farmer Dashboard** â€” fields, crops, tasks, health status at a glance
- **Weather Dashboard** â€” forecasts and AI-generated irrigation/field advisories
- **Crop Advisory** â€” crop-specific guidance by season and region
- **Disease Detection** â€” photo-based pest/disease identification with organic and chemical treatment options
- **Market Prices** â€” daily mandi prices by crop, market, and state
- **Government Schemes** â€” eligibility checking, benefits, and required documents
- **AI Chat Assistant** â€” bilingual conversational assistant with quick actions
- **Notifications** â€” weather, pest, scheme, task, and market alerts
- **Profile & Settings** â€” farmer profile, fields, and language preference

## Data Model

The Supabase schema (see [`docs/database`](./docs/database) for full documentation) currently includes:

`profiles`, `crops`, `fields`, `weather_logs`, `pest_scans`, `ai_conversations`, `ai_messages`, `schemes`, `scheme_documents`, `user_scheme_eligibility`, `market_prices`, `tasks`, `service_providers`, `notifications`, `reports`

All tables have Row Level Security enabled, and farmer-facing content is bilingual (`_hi` / `_en` columns).

## Repository Structure

```
.claude/          AI project memory: agents, skills, rules, prompts, commands, templates
.github/          Issue/PR templates, labels, CI workflows
docs/             Architecture, database, frontend, backend, and API documentation
components/       Reusable UI components (shadcn/ui-based)
hooks/            Custom React hooks
lib/              Shared utilities, Supabase client, AI clients
types/            Shared TypeScript types (including generated Supabase types)
public/           Static assets
scripts/          Build, seed, and maintenance scripts
tests/            Unit, integration, and e2e tests
```

## Getting Started

> This repository is being actively scaffolded â€” see [`ROADMAP.md`](./ROADMAP.md) for current stage.

```bash
git clone https://github.com/skavish601-cloud/Farmitra.ai.git
cd Farmitra.ai
npm install
cp .env.example .env.local   # fill in Supabase and AI provider keys
npm run dev
```

## Working with Claude Code

This repo is designed to be worked on with Claude Code. Start by reading [`CLAUDE.md`](./CLAUDE.md), which is the project's persistent memory: coding standards, architecture rules, naming conventions, and review/testing/security/performance/accessibility checklists.

Specialized agents live in [`.claude/agents/`](./.claude/agents) and reusable skills in [`.claude/skills/`](./.claude/skills) â€” see [`docs/agent-library.md`](./docs/agent-library.md) and [`docs/prompt-library.md`](./docs/prompt-library.md) once Stage 2â€“3 land.

## Contributing

See [`CONTRIBUTING.md`](./CONTRIBUTING.md).

## Security

See [`SECURITY.md`](./SECURITY.md) for how to report vulnerabilities.

## License

See [`LICENSE`](./LICENSE).
