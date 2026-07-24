# Database Schema

Live Supabase project: `farmmitra.ai` (ref `bunrdgbbsbzxakdfkgfa`). This document is the authoritative schema reference â€” keep it in sync with actual migrations.

## Conventions

- Tables and columns: `snake_case`
- Bilingual farmer-facing content: paired `<field>_hi` / `<field>_en` columns
- Every table: Row Level Security **enabled**, policies scoped to `auth.uid()` unless explicitly documented otherwise below
- Primary keys: `id` (UUID, default `gen_random_uuid()`) unless noted

## Tables

### `profiles`
Farmer user profile, one row per authenticated user. Linked to `auth.users` via `id`.

### `crops`
Reference data for crop types (bilingual and regional name, category, typical seasons).

### `fields`
A farmer's individual fields â€” owned by `profiles.id`, references `crops` for current crop.

### `weather_logs`
Weather data/history, associated with a field or region, used to generate advisories.

### `pest_scans`
Photo-based pest/disease detection records â€” owned by `profiles.id`, references a `fields` row, stores the AI diagnosis and confidence.

### `ai_conversations`
Chat assistant conversation threads â€” owned by `profiles.id`.

### `ai_messages`
Individual messages within an `ai_conversations` thread, role (user/assistant) and content.

### `schemes`
Government scheme reference data (bilingual name/description, eligibility criteria, benefits).

### `scheme_documents`
Documents required per scheme, linked to `schemes`.

### `user_scheme_eligibility`
Computed/stored eligibility result per farmer per scheme â€” owned by `profiles.id`, references `schemes`.

### `market_prices`
Mandi price records by crop, market, and date â€” references `crops`.

### `tasks`
Farmer task/reminder tracking â€” owned by `profiles.id`, optionally linked to a `fields` row.

### `service_providers`
Directory of dealers/technicians, searchable by region/service type.

### `notifications`
Weather/pest/scheme/task/market alerts â€” owned by `profiles.id`.

### `reports`
Generated/exportable reports (e.g. seasonal summaries) â€” owned by `profiles.id`.

## RLS Policy Pattern (default)

```sql
-- Example pattern applied per owned table
alter table public.<table> enable row level security;

create policy "Users can read own rows"
  on public.<table> for select
  using (auth.uid() = <owner_column>);

create policy "Users can insert own rows"
  on public.<table> for insert
  with check (auth.uid() = <owner_column>);

create policy "Users can update own rows"
  on public.<table> for update
  using (auth.uid() = <owner_column>);
```

Reference/shared tables (`crops`, `schemes`, `scheme_documents`, `market_prices`, `service_providers`) are typically **publicly readable, admin-write-only** â€” document any deviation from the owned-row pattern explicitly when the migration is written.

## Updating This Document

Every migration (Supabase Engineer's responsibility, see `.claude/agents/supabase-engineer.md`) should update this file in the same PR, including any new table, column, or policy change.
