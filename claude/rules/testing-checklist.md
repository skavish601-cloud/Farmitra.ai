# Checklist: Testing

- [ ] Unit tests for new `lib/` functions and hooks
- [ ] Component tests for interactive UI (forms, chat, dashboards)
- [ ] Edge cases covered: empty state, loading state, error state, offline/slow network
- [ ] RLS policies tested (a user cannot read/write another user's rows)
- [ ] AI provider calls are mocked in tests — no live API calls in CI
