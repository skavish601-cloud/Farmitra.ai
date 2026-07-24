# Prompt Library

Versioned reference for all AI-facing prompts used in FarmMitra. Source templates live in `.claude/prompts/` â€” this document is the human-readable, versioned index with rationale for changes.

## Chat Assistant System Prompt

**Current version:** v1 (2026-07-24)
**File:** `.claude/prompts/chat-assistant-system-prompt.md`
**Rationale:** Establishes bilingual response matching, conciseness for small-screen/outdoor reading, and a hard rule against inventing scheme amounts/prices/dosages.

## Disease Detection Prompt

**Current version:** v1 (2026-07-24)
**File:** `.claude/prompts/disease-detection-prompt.md`
**Rationale:** Requires explicit confidence framing and separates organic/chemical treatment options, with a safety nudge toward local expert verification before chemical application.

## Crop Advisory Prompt

**Current version:** v1 (2026-07-24)
**File:** `.claude/prompts/crop-advisory-prompt.md`
**Rationale:** Grounds advisory generation in region/season context and flags uncertainty in regional data rather than presenting generic advice as locally specific.

## Development Prompt Templates

Feature implementation, bug fix, and refactor templates are process prompts for working *on* the codebase (not AI-facing product prompts) â€” see `.claude/prompts/feature-implementation.md`, `bug-fix.md`, `refactor.md`.

## Change Process

Any change to a product-facing prompt (chat, disease detection, crop advisory):
1. Update the template in `.claude/prompts/`
2. Bump the version and add a dated entry with rationale here
3. Test against a fixed set of representative farmer queries before shipping (see `.claude/skills/prompt-engineering.md`)
4. Note any evaluation results (accuracy, cost, latency) in the entry
