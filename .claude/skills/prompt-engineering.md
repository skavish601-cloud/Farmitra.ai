# Skill: Prompt Engineering

## When to Use
Designing or modifying any AI-facing prompt (Chat Assistant, Disease Detection, Crop Advisory generation).

## Purpose
Reliable, grounded, bilingual AI behavior appropriate for farmers making real decisions.

## How to Apply
1. Be explicit about role, tone, and language-matching behavior (respond in the farmer's input language)
2. Instruct the model to say "not sure" rather than invent scheme amounts, prices, or dosages
3. Keep prompts concise and structured (role, constraints, output format) rather than long free-form instructions
4. Version prompts in `docs/prompt-library.md` with rationale for changes
5. Test prompt changes against a fixed set of representative farmer queries before shipping
6. Add confidence framing or "verify with a local expert" language for high-stakes outputs (chemical dosage, eligibility)

## Output Format
Versioned, documented prompts in `docs/prompt-library.md`, referenced from `lib/ai/`.

## Anti-patterns to Avoid
- Prompts that encourage confident guessing over stating uncertainty
- Unversioned prompt edits with no rationale recorded
- One giant prompt handling multiple unrelated tasks instead of task-specific prompts
