# Skill: Tailwind

## When to Use
All styling — no inline styles or separate CSS files except for genuinely global concerns.

## Purpose
Consistent, maintainable styling using Tailwind CSS and shadcn/ui.

## How to Apply
1. Use Tailwind utility classes directly in JSX
2. Use `cn()` (clsx + tailwind-merge) for conditional/merged class names
3. Prefer shadcn/ui primitives over custom-built equivalents
4. Support dark mode via Tailwind's `dark:` variant consistently across components
5. Use the project's design tokens (spacing, color, typography scale) rather than arbitrary values (`[13px]`) unless truly one-off

## Output Format
Utility-class-styled components consistent with the existing design system.

## Anti-patterns to Avoid
- Inline `style={{}}` props
- Arbitrary one-off values scattered instead of using/extending design tokens
- Duplicating a shadcn/ui component's functionality from scratch
