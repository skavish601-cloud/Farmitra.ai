# Memory: Product Context

FarmMitra AI is an AI-powered agriculture assistant for Indian farmers, available in Hindi, English, and Hinglish (BHASHINI planned for more languages).

**Target user:** often low-literacy, mobile-first, frequently working outdoors on mid-range Android devices with inconsistent connectivity. Design and engineering decisions should default to this user, not a desktop/high-bandwidth assumption.

**Core domains:**
- Fields & crops management
- Weather-linked advisories
- Pest/disease detection via photo upload
- Market (mandi) prices
- Government scheme eligibility
- AI chat assistant
- Notifications
- Farmer profile & settings

**What "done" looks like for a feature:** works correctly in Hindi and English, accessible (icon+text, WCAG AA contrast, keyboard nav), performant on 3G/4G and mid-range hardware, RLS-secured if it touches data, tested, and documented.

**What FarmMitra is *not*:** a general-purpose chatbot, a React Native mobile app (an earlier concept used this — superseded, see `CHANGELOG.md`), or a system that should ever guess at scheme amounts, prices, or chemical dosages rather than admit uncertainty.
