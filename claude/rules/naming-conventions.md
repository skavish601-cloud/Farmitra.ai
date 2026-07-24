# Rule: Naming Conventions

| Item | Convention | Example |
|---|---|---|
| Components | PascalCase, one per file | `WeatherCard.tsx` |
| Hooks | camelCase, `use` prefix | `useFieldData.ts` |
| Lib/service functions | camelCase, verb-first | `getMarketPrices()` |
| Types/interfaces | PascalCase | `FieldHealthStatus` |
| Supabase tables/columns | snake_case | `pest_scans`, `confidence_pct` |
| Bilingual columns | `<field>_hi` / `<field>_en` | `name_hi`, `name_en` |
| Route segments (App Router) | kebab-case | `app/crop-advisory/page.tsx` |
| Env vars | `SCREAMING_SNAKE_CASE`, `NEXT_PUBLIC_` only if client-safe | `NEXT_PUBLIC_SUPABASE_URL` |
| Branches | `<type>/<short-description>` | `feature/pest-scan-upload` |
| Commits | Conventional Commits | `feat(weather): add irrigation advisory card` |

Source of truth: `CLAUDE.md` §4.
