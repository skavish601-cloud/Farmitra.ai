# Component Guide

## Conventions

- One component per file, PascalCase filename matching the export (`WeatherCard.tsx`)
- Server Components by default; `"use client"` only when interactivity/hooks/browser APIs are required
- Built from shadcn/ui primitives where possible â€” check `components/ui/` before building a custom equivalent
- Every component handles loading, empty, and error states explicitly when it depends on async data
- Bilingual by construction â€” no hardcoded English-only strings; use `lib/i18n/`

## Directory Shape (as it fills in)

```
components/
  ui/                 shadcn/ui primitives (button, card, dialog, etc.)
  dashboard/           Farmer Dashboard widgets
  weather/             Weather Dashboard components
  crop-advisory/
  disease-detection/
  market-prices/
  schemes/
  chat/                AI Chat Assistant UI
  notifications/
  profile/
  shared/              Cross-feature shared components (language toggle, empty states, etc.)
```

## Adding a New Component

1. Check `components/shared/` and `components/ui/` for something reusable first
2. Place it under the feature folder it belongs to
3. Co-locate its test file
4. If it's genuinely cross-feature, put it in `components/shared/` instead of duplicating
5. Update this doc if you're introducing a new top-level feature folder
