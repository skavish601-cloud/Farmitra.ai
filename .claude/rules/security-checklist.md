# Checklist: Security

- [ ] RLS enabled on every table; policies scoped to `auth.uid()` where applicable
- [ ] No secret keys (AI provider keys, service role key) referenced from client-side code
- [ ] User input validated/sanitized before storage or before use in prompts
- [ ] File uploads size/type restricted and stored in access-controlled buckets
- [ ] Auth flows use Supabase Auth session handling, not custom token logic
- [ ] Dependencies checked for known vulnerabilities (`npm audit`) before release
