# Skill: Accessibility

## When to Use
Every UI change — accessibility is not a separate pass, it's part of implementation.

## Purpose
Usable UI for FarmMitra's target audience: often low-literacy, outdoor, mobile-first farmers, alongside standard WCAG compliance.

## How to Apply
1. Use semantic HTML and shadcn/ui primitives over custom divs
2. Ensure keyboard navigability and visible focus states on all interactive elements
3. Meet WCAG AA contrast — especially important for outdoor/sunlight mobile use
4. Pair icons with text labels — never icon-only controls, given the low-literacy audience
5. Associate form labels with inputs; ensure error messages are screen-reader announced
6. Keep the Hindi/English/Hinglish language toggle accessible from every primary screen

## Output Format
UI that passes the Accessibility Checklist in `CLAUDE.md`.

## Anti-patterns to Avoid
- Icon-only buttons/nav items
- Color as the only signal for state (error/success) without text or icon reinforcement
- Low-contrast text on outdoor-use screens
