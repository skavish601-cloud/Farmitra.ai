# Contributing to FarmMitra AI

Thanks for helping build FarmMitra AI. This guide covers how to set up the project, how we work, and what we expect from a pull request. Please also read [`CLAUDE.md`](./CLAUDE.md) — it defines the coding standards, architecture rules, and checklists referenced below.

---

## Code of Conduct

By participating, you agree to uphold our [Code of Conduct](./CODE_OF_CONDUCT.md).

## Ways to Contribute

- **Bug reports** — use the Bug issue template
- **Feature requests / ideas** — use the Feature issue template, or start a Discussion for anything open-ended
- **Code** — pick up an open issue (look for `good first issue` / `help wanted`) or propose your own via an issue first, so scope is agreed before you start
- **Documentation** — fixes and additions to `docs/` are always welcome, no issue required for small corrections

## Local Setup

```bash
git clone https://github.com/skavish601-cloud/Farmitra.ai.git
cd Farmitra.ai
npm install
cp .env.example .env.local
```

Fill in `.env.local` with:
- Supabase project URL and anon key (ask a maintainer for a dev project, or run your own via `supabase init`)
- AI provider keys (Claude / OpenAI / Gemini) as needed for the area you're working on — most UI work doesn't need these

```bash
npm run dev
```

## Branching & Commits

- Branch from `main`: `<type>/<short-description>`, e.g. `feature/pest-scan-upload`, `fix/weather-card-timezone`
- Use [Conventional Commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`
- Keep commits scoped and readable — squash noisy WIP commits before opening a PR if needed

## Making a Pull Request

1. Confirm your change is linked to an issue (open one first for anything non-trivial)
2. Include tests and documentation updates in the same PR — see the Testing and Documentation sections of `CLAUDE.md`
3. Run before opening the PR:
   ```bash
   npm run lint
   npm run typecheck
   npm run test
   npm run build
   ```
4. Fill out the PR template completely, including a summary of *why*, not just *what*
5. Request review; address feedback via new commits (don't force-push over review history mid-review)
6. A maintainer will squash-merge once CI is green and review is approved

## Pull Request Checklist

Before requesting review, confirm:

- [ ] Linked to an issue
- [ ] Follows naming conventions and architecture rules in `CLAUDE.md`
- [ ] Tests added/updated and passing
- [ ] Docs updated (`docs/`, and `CHANGELOG.md` if user-facing or breaking)
- [ ] No secrets, keys, or `.env` values committed
- [ ] RLS policies added/reviewed for any new or changed Supabase tables
- [ ] Accessibility and bilingual (Hindi/English) considerations addressed for UI changes

## Reporting Security Issues

Do **not** open a public issue for security vulnerabilities — see [`SECURITY.md`](./SECURITY.md) for how to report privately.

## Questions

Open a Discussion, or comment on the relevant issue. If you're unsure whether an idea fits the roadmap, check [`ROADMAP.md`](./ROADMAP.md) first.
