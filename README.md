# ðŸŒ¾ Farmitra AI

**An AI-powered companion for Indian farmers** â€” built on agricultural intelligence, Sarvam AI's Indian-language voice & text engine, and a Retrieval-Augmented Generation (RAG) layer over government agri-data.

> Farmitra ("Farm + Mitra") means *"friend of the farm"* in Hindi.

---

## What is Farmitra AI?

Farmitra AI is a mobile-first AI assistant that lets any Indian farmer ask questions in their own language â€” by voice or text â€” and get accurate, trustworthy answers about crops, weather, pests, government schemes, mandi (market) prices, and farming best practices.

Think of it as a WhatsApp-like chat, but the person on the other end is an AI agronomist who has read every government advisory, every crop guide, and every scheme document â€” and who also knows your field, your crop, and your local weather.

> "Farmitra AI turns scattered agricultural knowledge (government portals, crop science, market data) into one simple voice-and-text conversation a farmer can have in Hindi, Marathi, Tamil, or any of India's major languages."

### Built on three pillars

- **Farm Intelligence Engine** â€” crop/pest/disease identification, field data, agronomic reasoning, and document intelligence.
- **Sarvam AI** â€” the Indian-language layer: converts a farmer's spoken Hindi/Tamil/Telugu question into text, understands it, and replies back in natural speech in the same language.
- **A custom RAG Layer** â€” indexes government schemes, ICAR advisories, mandi prices, weather bulletins, and state agriculture department circulars, so every answer is grounded in real, current, citable information instead of the AI "guessing."

---

## The Problem

Indian farmers face an information gap, not an information shortage. The data already exists â€” on data.gov.in, Agmarknet, IMD, ICAR, state agriculture portals, PM-KISAN, and Kisan Call Centres â€” but it is scattered, in English or bureaucratic language, spread across dozens of websites and PDFs, and not accessible by voice in a farmer's own dialect.

- A farmer doesn't know which government scheme they qualify for, or how to apply.
- Pest and disease outbreaks are diagnosed late because expert advice is a phone call or a long trip away.
- Mandi prices change daily, but comparing markets to decide where and when to sell is hard.
- Most literacy-friendly tools assume typing and English, excluding a huge population who are more comfortable speaking than typing.
- Existing farm-advisory apps rarely combine live government data with personal field context in one place.

Farmitra AI closes this gap by being **voice-first, vernacular-first, and government-data-grounded**.

---

## Target Users

| User | What they need | How Farmitra helps |
|---|---|---|
| Smallholder farmer | Simple voice answers in mother tongue, no typing | Speak a question â†’ get a spoken answer + short text summary |
| Progressive / commercial farmer | Data-driven decisions, market timing | Price trends, weather-linked irrigation advice, yield forecasting |
| Agri-input dealers / FPOs | Bulk advisory for many farmers, scheme updates | Dashboard view, WhatsApp broadcast integration |
| Agricultural extension officers | Faster way to answer farmer queries at scale | Assistant + citation trail to verify government sources |
| NGOs / Govt agri departments | Distribute scheme information widely and reliably | API/embed Farmitra into their own citizen apps |

---

## Core Features

| Feature | Description | Powered by |
|---|---|---|
| Voice Q&A (Kisan Voice Chat) | Farmer speaks in Hindi/Tamil/etc., app replies with voice + text | Sarvam STT + LLM + Sarvam TTS |
| Crop & Pest Identification | Photo of a leaf/pest â†’ instant diagnosis and treatment steps | Farm-intelligence vision models |
| Government Scheme Finder | "Which subsidy can I get for a drip irrigation set?" â†’ direct, cited answer | RAG over govt scheme data |
| Mandi Price Tracker | "What is the onion price in Lasalgaon today?" answered instantly | Agmarknet / e-NAM data + RAG |
| Weather-Linked Advisory | "Should I irrigate today?" factors in live IMD forecast | IMD API + agronomic reasoning |
| Document Reader | Upload/photo a govt circular or soil health card; explained simply | Document intelligence + Sarvam Vision OCR |
| Multilingual Chat History | Every past conversation saved and searchable, per farmer, per field | App database |
| Community & Alerts | Push notifications for pest outbreaks, weather warnings, scheme deadlines | FCM + RAG alerts engine |
| Offline-lite Mode | Basic cached advisories available without internet | Local cache / PWA |

---

## System Architecture

The farmer's phone talks to a backend brain, which has three helpers â€” **Sarvam AI** (language), the **Agri-Intelligence engine** (farm intelligence), and our own **RAG engine** (government/market knowledge). The backend combines all three into one clear response.

| Layer | Role | Technology Choice |
|---|---|---|
| 1. Client (Farmer App) | Voice/text/photo input, audio playback, low-end Android support | React Native (Android-first) or Flutter; PWA fallback for feature phones via IVR/USSD |
| 2. API Gateway | Single entry point; auth, rate-limiting, routing | Node.js (NestJS) or FastAPI behind Nginx / AWS API Gateway |
| 3. Orchestration Service | The "brain" â€” routes and merges responses | Python (FastAPI) orchestrator, agent/router pattern |
| 4. Language Layer | STT, TTS, translation | Sarvam AI APIs â€” Saaras (STT), Bulbul (TTS), Mayura (Translation), Sarvam-30B/105B |
| 5. Agri-Intelligence Layer | Crop/pest ID, agronomic reasoning, document digitisation | Agri-intelligence API (Virtual Ag Expert, Weed/Insect/Fungus ID, Document Management) |
| 6. RAG Knowledge Layer | Retrieves relevant, current govt/agri passages | Vector DB + embeddings + retriever |
| 7. Data Sources | Live/static government/market/weather data | data.gov.in, Agmarknet, e-NAM, IMD, ICAR, PM-KISAN, state agri portals |
| 8. Storage | Farmer profiles, field data, chat history, cached answers | PostgreSQL + Vector DB + S3/Blob |
| 9. Infra & DevOps | Hosting, scaling, monitoring, CI/CD | AWS/GCP, Docker, Kubernetes (or ECS to start), GitHub Actions |

### Flow, in plain words

1. Farmer speaks into the app â†’ audio goes to the API Gateway.
2. Orchestrator sends audio to Sarvam Saaras (STT) â†’ clean text + English translation.
3. Orchestrator classifies intent: photo â†’ vision model; knowledge question â†’ RAG retrieval; live-data question â†’ direct API call.
4. Relevant government/agri passages are retrieved from the Vector DB and combined with agronomic reasoning.
5. An LLM (Sarvam-30B/105B or general model) drafts a grounded answer citing the source.
6. Sarvam Bulbul (TTS) converts the answer back into the farmer's language and voice.
7. App plays the audio and shows a short text + source-citation card.

---

## The RAG Engine

Instead of trusting the AI's memory (which can be outdated or wrong), Farmitra first searches trusted documents for the right facts, then asks the AI to write the answer using those facts â€” critical for things like scheme rules or subsidy amounts that change often.

### Knowledge base sources

- data.gov.in â€” open government datasets
- Agmarknet / e-NAM â€” daily mandi prices
- IMD â€” weather forecasts and agromet advisories
- ICAR & state agricultural universities (KVKs) â€” crop guides, pest/disease bulletins
- PM-KISAN, PMFBY, Soil Health Card, KCC â€” scheme rules, eligibility, application steps
- State agriculture department circulars
- Kisan Call Centre FAQ archives

### Pipeline

| Step | What happens |
|---|---|
| 1. Ingestion | Scheduled jobs pull PDFs, web pages, CSVs (daily for prices/weather, weekly for schemes/advisories) |
| 2. Cleaning & Chunking | Remove boilerplate; split into ~300â€“500 word chunks |
| 3. Embedding | Convert each chunk into a vector using an Indic-aware embedding model |
| 4. Storage | Vectors stored with metadata (source, date, language, region, scheme) |
| 5. Retrieval | Query embedded the same way; top 3â€“6 relevant chunks returned |
| 6. Re-ranking | Lightweight re-ranker filters out noise |
| 7. Generation | LLM answers only using retrieved chunks, citing source |
| 8. Citation | Final answer includes a short citation for verification |

### Recommended tools

- **Vector DB:** Pinecone or Qdrant (managed) â€” or pgvector inside PostgreSQL for a simpler MVP
- **Embeddings:** multilingual/Indic-aware embedding model
- **Orchestration:** LangChain or LlamaIndex
- **Scheduling:** cron (or Airflow as the pipeline grows)

> This RAG layer is Farmitra's real moat â€” anyone can call an LLM API, but few will have a clean, current, India-specific government-and-market knowledge base connected to it.

---

## Sarvam AI Integration

| Sarvam Model/API | What it does | Where Farmitra uses it |
|---|---|---|
| Saaras (STT) | Converts spoken question to text, 22+ Indian languages | Voice Q&A entry point |
| Bulbul (TTS) | Converts written answer to natural spoken audio | Voice answer playback |
| Mayura / Sarvam-Translate | Translates between Indian languages and English | Cross-language RAG search, document translation |
| Sarvam-30B / Sarvam-105B | Drafts grounded answers with strong Indian-language reasoning | Core conversation engine, paired with RAG |
| Sarvam Vision | Reads scanned/handwritten documents | Document Reader feature |

**Integration notes**

- Use the official `sarvamai` Python/JS SDK; API keys stay server-side, never in the mobile app.
- For real-time voice, pair Saaras (input) + Bulbul (output) in a streaming pipeline (REST, HTTP streaming, or WebSocket).
- Convert romanized "Hinglish" typed input to native script before sending to Bulbul for natural voice output.
- Sarvam's recommended pattern: Sarvam for Indian-language speech accuracy + a strong reasoning LLM + your RAG layer for complex answers â€” exactly Farmitra's design.
- Check the Sarvam Startup Programme for free API credits.

---

## Agri-Intelligence Layer

A farm-intelligence platform combines fine-tuned AI "experts" (agronomic research, regulatory product labels, weather data, GIS field geometry, crop-guide documents) with chat assistance, crop/pest/disease ID, document management, and field dashboards.

**Honest note:** public materials for such platforms often describe them as built primarily around a specific country's agriculture, and partner API access may not be fully open yet. Confirm current API availability, licensing, and Indian crop/region support directly with the provider before committing engineering time.

**Recommended approach**

- **Short term:** Use this as the reference pattern; integrate directly if partner API access is confirmed.
- **Parallel path:** Build/connect an India-specific agronomic layer using ICAR guides, KVK advisories, and an open-source or custom-trained plant/pest ID model so the roadmap isn't blocked.
- **Long term:** Use the partner API for its strongest capabilities as a value-added "expert-verified" layer once available.

This layer is interchangeable in the architecture â€” it can be swapped or supplemented (e.g. Plantix-style pest ID, custom vision models) without changing the rest of the system.

---

## Full Tech Stack

| Layer | Recommended Choice | Why |
|---|---|---|
| Mobile App | React Native (Android-first) | Covers 95%+ of Indian farmer smartphones |
| Lite/Offline Access | PWA + IVR/USSD fallback | Reaches feature-phone users |
| Backend API | Python (FastAPI) | Best ecosystem for AI/ML orchestration, RAG, async |
| Orchestration/Agents | LangChain / LlamaIndex | Ready-made RAG pipelines, retrievers, agent routing |
| Core Database | PostgreSQL | Reliable relational storage |
| Vector Database | Qdrant or Pinecone (or pgvector to start) | Fast semantic search |
| File/Media Storage | AWS S3 / GCP Cloud Storage | Store photos, audio, PDFs cheaply |
| Caching/Queue | Redis + Celery (or SQS) | Async jobs like TTS generation, data refresh |
| Language AI | Sarvam AI APIs | Indian-language STT, TTS, translation, LLM |
| Agri Intelligence | Partner API (pending confirmation) + India-specific fallback | Crop/pest ID, document intelligence |
| Live Data Feeds | data.gov.in, Agmarknet/e-NAM, IMD APIs | Fresh prices, weather, scheme data |
| Hosting/Infra | AWS or GCP, Docker + ECS/Kubernetes | Scales from MVP to millions of users |
| Monitoring | Grafana + Prometheus, Sentry | Uptime, latency, errors |
| CI/CD | GitHub Actions | Automated testing and deployment |
| Notifications | Firebase Cloud Messaging + WhatsApp Business API | Reach farmers where they already are |

---

## Example Data Flow

A farmer in Nashik speaks in Marathi: *"My onion crop has a disease, and is there any subsidy for treatment?"*

1. Farmer records a voice note (Marathi).
2. Audio â†’ Sarvam Saaras (STT) â†’ Marathi text + English translation.
3. Orchestrator detects two intents: (a) crop disease diagnosis, (b) subsidy question.
4. If a photo was attached, it goes to the vision model for disease identification.
5. The subsidy question triggers a RAG search over indexed scheme documents.
6. LLM combines the disease diagnosis + relevant subsidy passages into one clear answer (English internally).
7. Answer is translated back to Marathi and converted to speech via Sarvam Bulbul.
8. Farmer hears the spoken answer and sees a short text card with a "Source" link.
9. Conversation and recommended actions are saved to the farmer's profile for follow-up reminders.

---

## Database & Data Model (MVP)

- **users** â€” farmer_id, name, phone, preferred_language, location, farm_size
- **fields** â€” field_id, user_id, crop_type, sowing_date, GPS boundary, soil_type
- **conversations** â€” conversation_id, user_id, timestamp, input_type, transcript, response, sources_cited
- **knowledge_documents** â€” doc_id, source_name, source_url, category, region, published_date, raw_text
- **knowledge_chunks** â€” chunk_id, doc_id, text_chunk, embedding_vector, language
- **mandi_prices** â€” commodity, market_name, state, price_min, price_max, price_modal, date
- **alerts** â€” alert_id, region, type, message, valid_until
- **schemes** â€” scheme_id, name, eligibility_criteria, benefit_amount, application_steps, last_verified_date

Keeping `knowledge_documents`/`knowledge_chunks` separate from live transactional data (`mandi_prices`, `alerts`) makes it easier to refresh government data daily without touching the core RAG index.

---

## Roadmap

| Phase | Timeline | What to build |
|---|---|---|
| Phase 0 â€” Validation | Weeks 1â€“3 | Interview 30â€“50 farmers/FPOs; confirm top question types; confirm agri-intelligence API terms; shortlist data sources |
| Phase 1 â€” MVP | Weeks 4â€“10 | WhatsApp/simple app chatbot; voice Q&A in 2 languages; RAG over 2â€“3 sources; no photo ID yet |
| Phase 2 â€” Core Product | Weeks 11â€“20 | Native Android app; crop/pest photo ID; 5+ languages; weather-linked advisory; 8â€“10 data sources; offline-lite |
| Phase 3 â€” Scale | Weeks 21â€“32 | FPO/dealer dashboard; WhatsApp broadcast alerts; state govt pilot; 10+ languages; yield/price forecasting |
| Phase 4 â€” Ecosystem | 6+ months | Open API for NGOs/govt; marketplace tie-ins; deeper agri-intelligence partnership |

---

## Business Model

- **Freemium for farmers:** Core voice Q&A and scheme lookup free forever; premium tier for yield forecasting, priority support, unlimited photo diagnoses.
- **B2B2C via FPOs and input dealers:** Subscription dashboard for member farmers.
- **Government & NGO partnerships:** License RAG + voice layer as a citizen-facing scheme helpdesk.
- **Data & insights (anonymised, opt-in):** Aggregated regional crop-health/demand trends sold to agri-input companies and insurers.
- **Commission/referral:** Facilitate connections to insurance (PMFBY), seed/input suppliers, credit products.

> Any lending, insurance, or agri-input commerce feature involves financial and legal compliance â€” consult a lawyer before enabling monetary transactions.

---

## Team

| Role | Focus |
|---|---|
| Founder/PM | Vision, farmer research, partnerships, roadmap |
| Backend Engineer (Python) | API, orchestration, RAG pipeline, integrations |
| Mobile Engineer (React Native) | Farmer-facing app, offline mode, low-literacy UX |
| ML/AI Engineer | Embeddings, retrieval quality, prompt design, evaluation |
| Data Engineer (part-time initially) | Scraping/ingesting government sources |
| Agronomist / Domain Advisor | Validates AI answers, prevents harmful/incorrect advice |
| UI/UX Designer | Icon-based, voice-first, low-literacy-friendly design |
| Community/Field Ops | On-ground onboarding, feedback loops, FPO partnerships |

---

## Risks & Mitigations

| Risk | Mitigation |
|---|---|
| AI gives wrong or outdated advice | Cite sources; human-agronomist review loop for high-risk categories; label AI-generated content |
| Agri-intelligence API access limited | Confirm terms early; keep a parallel India-specific model path |
| Low smartphone/data access | WhatsApp/IVR/USSD-based lighter access alongside the app |
| Government data changes without notice | Automated re-ingestion jobs; "last verified" timestamp shown to users |
| Language coverage gaps | Start with top 5â€“6 languages, expand based on demand |
| Data privacy | Minimise data collection, clear consent, follow India's DPDP Act |
| Trust-building in rural communities | Partner with KVKs, FPOs, state agri departments |

---

## Next Steps â€” First 30 Days

- **Week 1:** Talk to 15â€“20 real farmers/FPOs; shortlist top 3 question categories.
- **Week 1:** Contact Sarvam AI for API access/Startup Programme credits; confirm agri-intelligence partner API terms.
- **Week 2:** Download sample datasets from data.gov.in, Agmarknet, and a state agriculture portal; test data quality.
- **Week 2:** Set up backend skeleton (FastAPI + PostgreSQL + vector DB) and an ingestion script for one data source.
- **Week 3:** Build a working prototype: WhatsApp/web chat â†’ Sarvam STT/LLM/TTS â†’ RAG over one dataset â†’ spoken answer.
- **Week 4:** Test with 10â€“15 real farmers; collect feedback on accuracy, voice quality, trust; iterate before building the full app.

---

## Disclaimer

This is a starting framework â€” validate every assumption (especially agri-intelligence API terms and government data licensing) with the actual providers before committing significant engineering time.

---

## License

TBD
