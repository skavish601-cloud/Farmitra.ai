# Skill: Internationalization (i18n)

## When to Use
Any farmer-facing content or UI copy.

## Purpose
Support Hindi, English, and Hinglish now, with BHASHINI-powered languages planned.

## How to Apply
1. Stored content (crops, schemes, pest names) uses paired `_hi`/`_en` database columns, not runtime translation
2. UI chrome/strings use the lightweight i18n dictionary in `lib/i18n/`
3. Design and build every primary screen with a visible, accessible language toggle
4. Handle Hinglish as an input variant for the AI Chat Assistant, not a separate stored language
5. When adding BHASHINI-supported languages, extend the dictionary/column pattern rather than introducing a parallel system

## Output Format
Content and UI that render correctly in all supported languages with no hardcoded English-only strings.

## Anti-patterns to Avoid
- Hardcoded English strings in components
- Runtime machine-translation of stored, reusable content instead of paired columns
- A language toggle that's present on some screens but not others
