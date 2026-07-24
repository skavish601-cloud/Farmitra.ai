# Skill: Planning

## When to Use
Before starting any feature, roadmap phase, or non-trivial bug fix â€” used primarily by the Planner agent, but any contributor can apply it before opening an issue.

## Purpose
Turn a vague request into scoped, sequenced, independently-shippable units of work.

## How to Apply
1. Restate the goal in one sentence â€” if you can't, the request needs clarifying first
2. List the layers touched (UI, hooks/lib, Supabase schema, Edge Functions, AI provider, docs)
3. Break work into units that can each be reviewed and merged independently
4. Order units by dependency (schema before UI that reads it; contract before implementation)
5. Note open questions explicitly rather than assuming an answer that changes scope
6. Map each unit to the responsible agent(s) from `.claude/agents/`

## Output Format
A numbered task list, each with: description, dependencies, owning agent, and acceptance criteria.

## Anti-patterns to Avoid
- Tasks that span multiple architectural layers in one PR
- Silent assumptions on ambiguous requirements
- Planning that turns into implementation before scope is agreed
