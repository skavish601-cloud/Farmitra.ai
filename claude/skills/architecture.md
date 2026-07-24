# Skill: Architecture

## When to Use
When a change introduces a new data flow, a new external dependency, or doesn't fit an existing pattern in the codebase.

## Purpose
Keep the system coherent: UI → hooks → `lib/` services → Supabase/AI clients, with clear placement of logic (client component, server component, Edge Function, or database trigger).

## How to Apply
1. Check `docs/architecture/` and existing code for a precedent before designing something new
2. Decide logic placement using these defaults:
   - Rendering/interactivity → Server Component, `"use client"` only if required
   - Anything needing a secret key → Edge Function / Route Handler
   - Data integrity rules → database constraint/trigger, not application code
   - Authorization → RLS policy, not application-layer checks alone
3. Write a short decision note (context, decision, consequence) in `docs/architecture/`
4. Define the interface/contract before implementation starts

## Output Format
A short ADR-style note plus a function/table/API contract other agents implement against.

## Anti-patterns to Avoid
- Replicating RLS logic in application code
- Novel patterns without documented justification
- Skipping the contract step and letting implementation define the interface ad hoc
