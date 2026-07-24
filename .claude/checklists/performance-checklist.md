# Checklist: Performance

- [ ] Server Components used by default; client bundle size checked for new client components
- [ ] Images use `next/image` with proper sizing
- [ ] Supabase queries select only needed columns; pagination used for lists
- [ ] Realtime subscriptions cleaned up on unmount
- [ ] AI calls show optimistic/loading UI â€” no blocking spinners over 300ms without feedback
