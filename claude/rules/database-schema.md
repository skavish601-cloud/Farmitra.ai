# Memory: Database Schema Snapshot

This is a quick-reference snapshot of the live Supabase schema. Treat `docs/database/` as the authoritative, detailed source — update both when the schema changes.

**Tables (public schema, all RLS-enabled, bilingual where farmer-facing):**

| Table | Purpose |
|---|---|
| `profiles` | Farmer user profiles |
| `crops` | Crop reference data |
| `fields` | A farmer's fields |
| `weather_logs` | Weather data/history per field or region |
| `pest_scans` | Photo-based pest/disease detection records |
| `ai_conversations` | Chat assistant conversation threads |
| `ai_messages` | Individual chat messages |
| `schemes` | Government scheme reference data |
| `scheme_documents` | Documents required per scheme |
| `user_scheme_eligibility` | Computed/stored eligibility per farmer |
| `market_prices` | Mandi prices by crop/market/date |
| `tasks` | Farmer task/reminder tracking |
| `service_providers` | Dealers/technicians directory |
| `notifications` | Weather/pest/scheme/task/market alerts |
| `reports` | Generated/exportable reports |

**Conventions:** snake_case tables/columns; bilingual fields as `<field>_hi` / `<field>_en`; RLS policies scoped to `auth.uid()` unless documented otherwise in `docs/database/`.
