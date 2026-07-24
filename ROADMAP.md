# FarmMitra AI — Roadmap

This roadmap tracks both the **repository transformation** (adopting the Everything Claude Code structure) and the **product build-out**. It will be updated as stages complete — see `CHANGELOG.md` for a dated history of what's shipped.

---

## Repository Transformation Stages

| Stage | Status | Deliverable |
|---|---|---|
| 1 | 🟡 In progress | Repo skeleton — folder structure, `README.md`, `CLAUDE.md`, `CONTRIBUTING.md`, `ROADMAP.md`, `SECURITY.md`, `CHANGELOG.md`, `CODE_OF_CONDUCT.md` |
| 2 | ⬜ Not started | `.claude/agents/` — 15 specialized agents (Planner, Architect, Frontend/Backend/Supabase Engineer, UI Designer, AI Engineer, Testing/Security/Performance Engineer, Documentation Engineer, GitHub Engineer, Reviewer, Refactoring Engineer, Release Manager) |
| 3 | ⬜ Not started | `.claude/skills/` — 18 reusable skills (planning, architecture, debugging, refactoring, testing, docs, GitHub, code review, Supabase, React, Next.js, TypeScript, Tailwind, accessibility, performance, security, i18n, prompt engineering) |
| 4 | ⬜ Not started | `.claude/rules/`, `.claude/memory/`, prompt templates, checklists |
| 5 | ⬜ Not started | `.github/` — issue templates, PR template, labels, milestones, Actions workflows (lint, typecheck, test, build, deploy, doc checks) |
| 6 | ⬜ Not started | `docs/` — architecture, database, API, components, deployment, environment variables |
| 7 | ⬜ Not started | Next.js app scaffold, Supabase generated types, first dashboard components |

---

## Product Roadmap

### Phase 0 — Foundation (current)
- Repository and AI-development scaffold (Stages 1–7 above)
- Supabase schema finalized for MVP tables (done: `profiles`, `crops`, `fields`, `weather_logs`, `pest_scans`, `ai_conversations`/`ai_messages`, `schemes`/`scheme_documents`/`user_scheme_eligibility`, `market_prices`, `tasks`, `service_providers`, `notifications`, `reports`)
- Auth flow (Supabase Auth) and base app shell

### Phase 1 — MVP
- Farmer Dashboard (fields, crops, tasks overview)
- AI Chat Assistant (bilingual, Hindi/English/Hinglish)
- Weather Dashboard with basic advisory
- Government Scheme Finder (eligibility lookup against `schemes` data)
- Market Prices view

### Phase 2 — Core Product
- Disease Detection (photo upload → `pest_scans`, organic/chemical treatment suggestions)
- Notifications (weather, pest, scheme, task, market alerts)
- Profile & Settings, language preference
- Service provider directory (dealers, technicians)
- Reports export

### Phase 3 — Scale
- BHASHINI integration for additional Indian languages
- Realtime notifications via Supabase Realtime
- Offline-lite / PWA support
- Performance and accessibility hardening for low-end Android devices

### Phase 4 — Ecosystem
- Public/partner API for NGOs and government agri-departments
- FPO / dealer dashboard and bulk advisory tools
- Deeper AI grounding (RAG over government scheme/advisory documents)

---

## How This Roadmap Is Maintained

- Updated at the end of each completed stage or phase
- Any change affecting scope should be reflected here in the same PR (see `CONTRIBUTING.md`)
- Longer-term ideas that aren't yet scheduled belong in GitHub Discussions, not this file
