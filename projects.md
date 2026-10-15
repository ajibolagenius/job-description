# Project dossier — Ajibola Akelebe

Every project on https://ajibolagenius.vercel.app/projects, verified 2026-10-08. The **Narvo family
(Tier 2) was re-verified 2026-10-14 directly from the now-public GitHub repos**, which is why its stacks
read in more detail than the rest of the file.
Site's own database holds **25 projects & sandbox toys** (23 listed on `/projects` + Color Lab and Mesh Lab on `/sandbox`). Roles, durations, and stacks
are as stated on each project page — quote them, don't embellish them.

⚠️ **Repos marked PRIVATE return 404 publicly.** Never link them in an application. Cite the live
URL or the portfolio project page instead. (Checked 2026-10-14: `zora`, `hekaiq`, `negotivity`,
`sonasdigital`, `Job-Hustles-Recruiting-Platform`, `Narvo-Intelligence/narvo_intelligence` and
`Narvo-Intelligence/documentations` are private; every other repo named public below was confirmed
reachable without authentication.)

**Changelog**

- **2026-10-14** — **Narvo-Intelligence repos went public.** `narvo_news`, `narvo_platform`, `legacy_code_2` and `narvo-app-proto` now return 200 anonymously and are safe to link; `narvo_intelligence` and `documentations` still 404. Tier 2 rewritten from repo source (package.json, `requirements.txt`, `server.py`, migrations, CI, Dockerfiles, READMEs), not from the portfolio page. Added the **Narvo API** dossier — the shipping FastAPI/Python 3.12 backend on Docker + Google Cloud Run, with Gemini/Groq LLM fallbacks, YarnGPT/Google/OpenAI TTS fallbacks, Upstash Redis, Vector and QStash signed cron, pywebpush, Supabase RLS migrations and a Deno edge function, 35 pytest modules, mypy and pyright. Added the **Narvo app prototype** (build-free HTML/CSS/JS, eight sprints, PWA, NDPA legal pages). Corrected Narvo News to what the monorepo actually contains (pnpm workspaces, `@narvo/mocks`, hand-written service worker, Actions CI) and flagged its migration-phase status. Private-repo count 8 → 7.
- **2026-10-08** — New page **Branda V2** (`/projects/branda-v2`): four-market service-ordering storefront (NG/US/UK/CA), built solo in **24 hours**, public repo `branda-v2-frontend`, live at https://branda-v2-theta.vercel.app; now first on the CV's Selected Projects. Portfolio repo corrected to the public `ajibolagenius/ajibolagenius` (the old `ajibola-portfolio` URL 404s). Portfolio gained the **Naija Vintage Radio** cassette player, **EN/YÓ (Yoruba) language switcher**, and **PostHog** analytics with owner-visit exclusion.
- **2026-09-10** — New page **Vertex** (`/projects/vertex`): AI-driven learning platform on Sanity + GROQ + Sanity Context MCP, public repo `vertex-lms`, live at https://vertex-lms-app.vercel.app. First Sanity/headless-CMS, Clerk and PostHog evidence in the portfolio — claim it as a shipped side project.
- **2026-09-09** — Shipped **"Match My Job Description"** AI recruiter mode (`matchJobDescription` tool in the AI assistant and Command Palette), **Tactile Micro-Audio** (zero-asset Web Audio synthesis via `sound.ts`, global SoundToggle), and the **Interactive System Architecture Visualizer** (`architecture-visualizer.tsx`, packet simulation for Zora Market and AfroGraph). Canonical title confirmed **Full Stack Engineer** across platforms. Mesh Lab, Notes/Writing, Command Palette (⌘K), View Transitions API and the OKLCH/P3 design system remain as previously recorded.
- **Site-vs-rules conflict, worth knowing before a recruiter checks:** the Fidia page on the site labels the role "Co-founder & Design Lead". Applications must still say **"Co-Founder & Brand/Visual Designer"** per the Medium post-mortem (see `profile.md`). Don't elevate the claim just because the page does.

---

## Tier 1 — commerce and money (lead with these for most roles)

### ⭐ Zora Market — Mobile App  *(the strongest item in the portfolio)*
- **Tagline:** Customer-facing iOS and Android app for the Zora marketplace.
- **Role:** Mobile Engineer — React Native & Expo · **4 months** · 2026 · Client (Mobile)
- **Categories:** Mobile App, E-commerce, Marketplace
- **LIVE ON APP STORE + GOOGLE PLAY:**
  - Apple: https://apps.apple.com/us/app/zora-market/id6764317880 — v1.0.14 · Shopping · first released **2026-04-30** · latest version 2026-06-12 · free · iOS 15.1+ · 127 supported devices
  - Google Play: https://play.google.com/store/apps/details?id=com.zoraapp.zoramarket — per user confirmation **2026-08-14** (treat as ground truth; not independently re-scraped)
  - Published under the client's developer account, **ZORA AFRICA LIMITED** — he is the engineer, not the publisher. Phrase accordingly.
  - **0 ratings / 0 reviews.** Never imply downloads, traction, or user numbers.
  - Safe phrasing: "live on the App Store and Google Play" or "built for iOS and Android, shipped on both stores."
- **Problem:** "Diaspora shoppers buy groceries on their phones, in short bursts, often on patchy connections. A responsive web storefront could not give that audience what it expects from a shopping app." Multi-vendor baskets also had to stay legible so shoppers never lose track of item origin.
- **Solution:** A single Expo codebase sharing TypeScript types and the API client with the web surfaces. TanStack Query with AsyncStorage persistence for offline browsing, Zustand with MMKV for cart and auth state, Supabase for auth/data/realtime, and Stripe React Native for native payment sheets. The cart groups items by vendor for clarity.
- **Stack:** Expo SDK 55, React Native 0.83, Expo Router, NativeWind, Tailwind CSS, Supabase, Stripe React Native, TanStack Query, Zustand, MMKV, Reanimated, expo-local-authentication, expo-notifications, Expo Updates, EAS, React Native Maps, React Hook Form, Zod, TypeScript
- **Features:** biometric sign-in (Face ID/Touch ID) · cart that survives a killed app · offline browsing · multi-vendor checkout with grouped shipping · native payment sheets (Apple Pay/Google Pay) · live order tracking over Supabase realtime · push notifications · over-the-air updates · guest browsing
- **Repo:** `ajibolagenius/zora` — **PRIVATE**
- **Use for:** ⭐ any mobile or React Native role; consumer product; e-commerce and checkout; offline-first and low-bandwidth engineering; native platform APIs (biometrics, push, OTA); release engineering and app-store review. This is the one credential most applicants can't match — an app that passed review and ships updates.

### Zora African Market  *(the web and backend half — same product, sibling page)*
- **Tagline:** A multi-surface marketplace connecting the African diaspora with authentic groceries and products from verified vendors.
- **Role:** Full-stack Engineer — Mobile, Web & Backend · **4 months** · 2026 · Client · Featured
- **Problem:** Diaspora customers struggle to buy authentic African groceries from trustworthy vendors in one place; sellers need operational tools; operators need moderation and platform controls — normally fragmented across separate systems.
- **Solution:** Unified shopping on iOS/Android with biometric auth and region-based discovery, vendor onboarding through the marketing site, and operational dashboards for vendors and admins. Shared TypeScript packages and a single Supabase backend keep data coherent across every surface.
- **Surfaces:** React Native (Expo) customer app · Next.js marketing site with vendor onboarding · vendor dashboard · admin dashboard
- **Stack:** Next.js 15, React Native & Expo, Supabase, Stripe, TanStack Query, Zustand, Tailwind CSS, shadcn/ui, NativeWind, Turborepo, TypeScript, React Hook Form, Zod, Google Maps
- **Features:** multi-vendor checkout · regional delivery · biometric authentication · **inventory management** · vendor onboarding · admin governance dashboards · real-time cart sync · payment processing
- **Live:** https://zoraapp.co.uk · **Repo: PRIVATE**
- **Use for:** e-commerce, marketplaces, inventory, logistics, admin tooling, mobile+web from one codebase, monorepo architecture, payments.
- **Pairing note:** this page and the mobile-app page above are the same product from two angles. Cite **both together** to show end-to-end range — "one Turborepo, one Supabase backend, five surfaces: an App Store iOS app, a marketing site with vendor onboarding, a vendor dashboard, and an admin dashboard." Don't present them as two unrelated projects; a hiring manager who clicks both will notice.

### Nego — Premium Managed Talent Marketplace
- **Tagline:** Elite marketplace connecting discerning clients with vetted, world-class talent.
- **Role:** Developer & Designer · **3 months** · 2026 · Client · Live
- **Problem:** Securing high-value transactions and premium media while maintaining an elite user experience; discretion and escrow reliability were critical.
- **Solution:** Custom **"Empire Wallet"** with Paystack-backed coin purchases and **automated escrow**. Tiered Client/Talent/Admin dashboards for real-time booking, secure media unlocking via Cloudinary, and admin verification workflows.
- **Stack:** Next.js 16, Supabase, Tailwind CSS 4, Cloudinary, Paystack, Resend, Phosphor
- **Live:** https://www.negoempire.live · **Repo (public):** https://github.com/ajibolagenius/nego
- **Use for:** payments, wallets, escrow, financial flows, role-based dashboards, verification/moderation workflows, two-sided marketplaces.
- **Caution:** the marketplace is adult-adjacent (companionship bookings — corporate events, dinner dates). Lead with the *technical* substance — wallet, escrow, Paystack, tiered access control — and omit the vertical unless it's relevant. For conservative or family-brand employers, prefer Zora as the payments example.

### NEGOtivity | Street-Wise Clothing
- **Tagline:** Premium, street-wise apparel storefront, a sub-brand of NEGO.
- **Role:** Developer & Designer · **1 month** · 2026 · Client · Featured
- **Problem:** NEGO had a talent marketplace but no dedicated storefront for its clothing sub-brand that authentically carried its premium street aesthetic.
- **Features:** high-fidelity animations · responsive **Figma-accurate** layouts · **Nigeria-focused currency system** · comprehensive theme support
- **Stack:** React, Next.js, Cloudflare, Supabase, GSAP, Lucide, Lenis, Resend, Zustand, Tailwind CSS, Wrangler, ESLint, TypeScript
- **Live:** https://negotivity.com · **Repo: PRIVATE**
- **Use for:** ⭐ **the single best proof for any fashion, apparel, or retail-brand role.** Also design-to-code fidelity, Naira/currency handling, storefront UX.

### Branda V2 — Multi-Market Service Ordering Storefront
- **Tagline:** "A service ordering interface for Branda, a Nigerian branding company, built in 24 hours as a frontend screening task."
- **Role:** Solo Developer · **24 hours** · 2026 · Side · Live · Featured (homepage reel)
- **Categories (site):** E-commerce, Multi-market Storefront, Branding Services
- **Problem:** Branda's existing site served Nigeria only with naira pricing, lacked international SEO, and loaded slowly on mobile. Brief: a four-region interface inside 24 hours.
- **Solution:** Market subfolders `/ng`, `/us`, `/uk`, `/ca`, each with its own currency, tax, delivery fee and free-delivery threshold; switching market keeps the same page and filters. Server Components by default (static market home and service pages per market, per-request catalogue). Catalogue across five studios (Create, Prints, Gifts, Studio, Digital) with word-matching search, industry/turnaround/use-case filters, sorting and pagination — **every filter lives in the URL**, so results are shareable and indexable. Service pages with live option pricing; one `orderSummary()` function owns subtotal/tax/delivery/total for drawer, cart and checkout, covered by Node test runner checks. Zustand cart persisted to the browser, hydration-safe. **Native HTML over libraries:** `<dialog>` cart, popover API for search and mobile menu, `<select>` market switcher, radio-input options. CSS-only motion, all reduced-motion aware. Loading skeletons, error boundary with retry, styled 404, designed empty states. Mock checkout — no payment taken.
- **SEO:** per-page titles/descriptions, canonical + `hreflang` for all four markets, Product structured data, sitemap, `robots.txt`.
- **Stack:** Next.js 16 (App Router), React, TypeScript, Tailwind CSS v4, Zustand, Lucide React, Node test runner, Vercel
- **Live:** https://branda-v2-theta.vercel.app (redirects to `/ng`) · **Repo (public):** https://github.com/ajibolagenius/branda-v2-frontend — README carries the written answers (performance, architecture, site review).
- **Use for:** ⭐ multi-market / multi-currency / international e-commerce, technical SEO (hreflang, structured data), Server Components rendering strategy, URL-as-state, native-HTML accessibility, testing money logic, and speed (**24 hours**, faster than Hotbite).
- **Caution:** it was a **hiring screening task**, not a client engagement. Branda did not commission or ship it. Say "built a four-market storefront in 24 hours" — never "built for Branda" or "Branda's new site", and never imply payments processed (checkout is mocked).

### Heka IQ
- **Tagline:** An automated football prediction platform designed for the African market.
- **Role:** Full-stack Engineer — Mobile · **6 weeks** · 2026 · Side · In Progress
- **Problem:** Nigerian football fans have no platform that rewards genuine tactical skill — they're scattered across risky betting sites, time-heavy fantasy leagues, and informal group chats with no transparent peer-to-peer prediction.
- **Solution:** Offline-first PWA plus native mobile, a proprietary **"Sphinx"** CatBoost ML model for users to challenge, custom fan hubs with real-time duels, transparent pool-staking and cross-currency duels, Paystack local payments, and IndexedDB caching tuned for 3G.
- **Stack:** Next.js 15, TypeScript, Supabase, Expo, CatBoost, Zustand, PWA, Paystack, Phosphor Icons, Dexie.js
- **Repo: PRIVATE**
- **Use for:** ML in production, offline-first and low-bandwidth engineering, Paystack, real-time features, mobile.

---

## Tier 2 — the Narvo product family (platform, AI, B2B, docs)

His GitHub company field is `@narvo_news`; these live under the `Narvo-Intelligence` org.

⚠️ **Visibility changed 2026-10-14.** Verified by anonymous HTTP request (200 without auth):
**`narvo_news`, `narvo_platform`, `legacy_code_2` (the shipping Narvo API) and `narvo-app-proto` are now
PUBLIC and safe to link.** Still 404 for outsiders: `narvo_intelligence` and `documentations` — never
link those two. Everything below was read from the repo source on 2026-10-14, not from the portfolio
page, so the stacks are exact.

**One honest status caveat that must survive into any letter.** `narvo_news` is the **migration target**:
its README states the backend is *"not scaffolded yet"* and both apps consume `@narvo/mocks` as the
"single Zod-validated fixture source for the migration phase", with the next step recorded as "wire
Supabase Auth + FastAPI". The **shipping** Python/FastAPI pipeline is the `legacy_code_2` repo. So:
cite `narvo.news` as the live product, cite the FastAPI backend from `legacy_code_2`, and never claim
the consumer monorepo is serving live data from its own API.

### Narvo News — consumer app surfaces (public monorepo)
- **Tagline:** Consumer B2C surfaces for Narvo, transforming daily news feeds into localized, high-quality audio briefings using speech synthesis and AI narrative alignment.
- **Role:** Full-stack Engineer · **18 months** · 2026 · In Progress
- **Problem:** African news platforms are text-heavy, ignore local dialects and language barriers, and add friction through data constraints and weak reporting transparency.
- **Solution:** Multilingual audio-first PWA with AI translation across **five languages (Yorùbá, Igbo, Hausa, Pidgin, English)**, high-quality TTS, thumb-first mobile interface, offline access, and a **Provenance/Truth Tag** system tracking AI consensus for source transparency. Two separately deployed web properties from one workspace: the signed-in `narvo.news` shell and `narvo.live`, an auth-free listen-now and share-clip surface whose routes cross-link back.
- **Repo-verified engineering (2026-10-14):**
  - **pnpm 9 workspace monorepo**, two Next.js apps (`frontend` port 3000, `live` port 3001) plus a shared **`@narvo/mocks`** package of Zod schemas and fixtures (`data`, `onboarding`, `plans`); one `styles/b2c-tokens.css` design-token file shared by both apps; parallel `pnpm dev`, recursive `typecheck`, per-app `build` scripts.
  - **Next.js 16.2.4, React 19.2.4, Tailwind CSS v4, Zod 3.25, Phosphor Icons, ESLint 9, TypeScript 5, Node 20.**
  - **App Router route groups** separating surfaces: `(marketing)`, `(auth)`, `(app)` shell (home, discover, listen, library, briefing, search, story/[id], channel, plans, checkout with success and cancel routes, profile sub-routes for account, billing, voice, preferences, privacy), a 7-step `onboarding/` wizard, and `auth/` reset, verify and callback routes.
  - **PWA**: `manifest.json`, a hand-written `sw.js` (cache-first app shell, network-first navigations, `/offline.html` fallback over a declared 20+ route shell list), and a `pwa-registration` component.
  - **CI**: GitHub Actions on push and PR — `pnpm install --frozen-lockfile`, lint, typecheck, build, with concurrency groups and `cancel-in-progress`.
  - **Deployment**: separate Vercel projects per app, cross-linked through `NEXT_PUBLIC_LIVE_URL` / `NEXT_PUBLIC_NARVO_NEWS_URL`.
- **Stack:** Next.js 16, React 19, TypeScript, pnpm workspaces, Tailwind CSS v4, Zod, PWA (manifest + service worker), Phosphor Icons, GitHub Actions, Vercel
- **Live:** https://narvo.news · **Repo (public, safe to link):** https://github.com/Narvo-Intelligence/narvo_news
- **Use for:** monorepo architecture, shared design tokens and typed fixture contracts, PWA install and offline strategy, App Router information architecture, CI quality gates, audio-first product thinking, localisation, long-term ownership.

### ⭐ Narvo API — the shipping AI audio pipeline (public Python backend)
*The single best proof he has of production Python backend engineering, and a recruiter can now read the code. Lead with this for any backend, AI-infrastructure or platform role.*
- **Tagline:** Broadcast-grade news API: narrative synthesis, translation, TTS, fact-check, briefings and personal-domain endpoints behind one FastAPI service.
- **Role:** Full-stack Engineer — backend and pipeline · 2026 · part of the Narvo product family
- **Repo (public, safe to link):** https://github.com/Narvo-Intelligence/legacy_code_2 — the name is a holding label for the shipping v5 codebase; in a letter call it **"the Narvo API"**, not "legacy code".
- **Stack, verbatim from the repo README's stack table:** Frontend Next.js 15, React 19, Tailwind CSS v4 · Backend **FastAPI, Python 3.12** · Auth and database **Supabase** · Primary LLM **Gemini**, fallback **Groq** · Primary TTS **YarnGPT**, fallback **Google Cloud TTS, then OpenAI** · Frontend hosting **Vercel**, backend hosting **Google Cloud Run**.
- **Service architecture:** one FastAPI app assembled in `server.py` from **16 route modules** (`news`, `search`, `briefing`, `translation`, `tts`, `factcheck`, `discover`, `me`, `admin`, `billing`, `feedback`, `notifications`, `share`, `aggregators`, `cron_tasks`, `health`) over **25 service modules** (narrative, translation, tts, yarngpt, llm_gemini, llm_groq, briefing, factcheck, recommendation, podcast, radio, offline, story_content, subscription, push_sender, push_payloads, provider_status, ssml_decorator, sound_themes, aggregator, article_scraper, admin, user, news, tts_cache_cleanup), with `lib/` clients for supabase_db, redis_client, vector_client, ratelimit, cache_registry, auth, http_client, audio_storage, text_utils, qstash_verify, gcp_verify, env_check. Annotated "monolith decomposition" in source.
- **HTTP contract, written by hand:**
  - Middleware stack: GZip (500 B minimum) · request-ID middleware that mints or adopts `X-Request-ID`, times every request, and logs method/path/status/latency · **structured JSON logging** formatted specifically for Cloud Run and container log ingestion, with `request_id`, `user_id`, `latency_ms` fields and noisy HTTP libraries quieted to WARNING · **security headers** (`X-Content-Type-Options: nosniff`, `X-Frame-Options: DENY`, `Referrer-Policy`, and a `Content-Security-Policy` with an explicit `connect-src` allow-list of Supabase, Upstash, YarnGPT, OpenAI and Google endpoints) · **rate limiting** keyed on authenticated user id, falling back to the leftmost `X-Forwarded-For` IP, returning a 429 inside the standard envelope.
  - One **standardised error envelope** (`error`, `code`, `detail`, `status`, `request_id`, `user_id`) with handlers for `HTTPException`, framework `StarletteHTTPException` (so 404/405 normalise too), and a fallback 500 handler that logs with context.
  - OpenAPI kept, `docs_url=None` replaced by a **custom-themed Swagger UI** page; API version `2.0.1` with a `scripts/bump_api_version.py` release helper.
- **Scheduled and asynchronous work:** **Upstash QStash** fires the Morning Briefing cron (`/api/briefing/cron`) and a weekly TTS-cache cleanup route; inbound QStash requests are **signature-verified** against current *and* next signing keys so key rotation causes no downtime, with a bearer/`X-Cron-Secret` fallback for local runs. Briefing completion fans out to **web push** via `pywebpush` with VAPID keys and push-subscription tables.
- **AI and data plumbing:** Gemini for narrative, translation, briefing and recommendations with **Groq as the declared secondary**; **YarnGPT as primary TTS for Nigerian voices (Yoruba, Igbo, Hausa, Pidgin, English)** with OpenAI and Google Cloud TTS as fallbacks, plus an **SSML decorator** service and a **TTS cache** with scheduled row cleanup; a **provider-status** service for health across providers; **Upstash Vector semantic recommendations** with the index dimension pinned to 768 to match Gemini's `output_dimensionality`; Upstash Redis plus a cache registry for hot reads; Google Fact Check API and Podcast Index where keys exist; radio-browser.info for live radio.
- **Ingestion pipeline:** `feedparser` for RSS plus four article-extraction libraries (`trafilatura`, `newspaper4k`, `readability-lxml`, `goose3`) over `aiohttp`/`httpx` with `tenacity` retry, feeding the aggregator, scraper and story-content services and a scraped-articles table with its own migration.
- **Data layer:** Supabase Postgres with **numbered migrations including `005_rls_policies.sql`** — user-scoped tables for briefings, bookmarks, offline articles, listening history, user preferences, push subscriptions, feedback, source reputation and story content; **JSONB columns for per-language translations and `audio_by_lang`**; SHA-1-hashed story ids; `timestamptz` defaults; documented convention that **RLS is mandatory on every new table** with `auth.uid() = user_id` for private rows. A **Deno Supabase Edge Function** (`supabase/functions/narvo-news-edge`) sits alongside. Supabase Storage for audio with `public, max-age=31536000, immutable` so repeat plays hit the CDN edge, auto-created buckets, and a data-URL path when storage is disabled.
- **Auth and security:** Supabase JWT verification using the project JWT secret for all `/api/me/*` and Bearer routes, `gcp_verify` for Google identity tokens, `qstash_verify` for cron webhooks, `bcrypt`/`passlib`/`python-jose`/`PyJWT`/`cryptography` in requirements, plus a dedicated `test_security_fixes.py`.
- **Testing and quality gates:** **pytest + pytest-asyncio across 35 test modules** (API smoke, launch smoke, auth, admin and fact-check APIs, aggregator integration and Redis keys, AI sanitizer, i18n settings, offline user scoping, persistence, provider health, recommendation, SSML decorator, translation-factcheck, TTS-podcast-aggregator, share payload helpers, truth tags, push); `mypy` **and** a `pyrightconfig.json`; `black`, `isort`, `flake8`; `pytest.ini` pinning `testpaths`.
- **Container and deploy:** `Dockerfile` on `python:3.12-slim`, dependency layer cached first, `entrypoint.sh`, `PORT` respected from the Cloud Run injector, 8080 exposed, and a root-level Dockerfile whose header states it builds **from the repo root for Cloud Build** onto **Google Cloud Run**. Sentry initialised with `traces_sample_rate=0.1` and environment tagging. `stripe` in requirements behind a `billing` route.
- **Its consumer frontend, in the same repo:** Next.js 15.4, React 19.2, Tailwind 4.1.11, `motion` 12, a shadcn-style class stack (`class-variance-authority`, `clsx`, `tailwind-merge`, `lucide-react`), React Hook Form with Zod resolvers, Supabase client, `middleware.ts`, realtime hooks (`useListeningHistoryRealtime`, `useUserTableRealtime`), a `use-prefers-reduced-motion` hook, offline cloud sync and IndexedDB storage, playback continuity, prefetch-audio, an analytics module and a feature tour. A separate `investor/` Next.js 15 site (React 18, better-sqlite3) lives beside them.
- **Use for:** ⭐ Python and FastAPI backends, API design and contract discipline (error envelopes, request IDs, versioned docs), LLM and TTS provider orchestration with fallbacks, RAG-style semantic recommendation via vector indexes, scheduled jobs and signed webhook ingestion, push infrastructure, Postgres schema/RLS design, JSONB multilingual storage, CDN-aware media delivery, pytest quality gates, Docker and GCP Cloud Run deploys, scraping and ETL pipelines.

### Narvo app prototype (public, build-free)
- **Tagline:** Single vanilla HTML/CSS/JS prototype for the entire Narvo consumer app — marketing, auth, onboarding, app shell and audio player, with no build step.
- **Role:** Solo Designer & Developer · 2026 · Side · **Public repo, no deployment needed**
- **Repo (public, safe to link):** https://github.com/Narvo-Intelligence/narvo-app-proto
- **What it proves, from its own sprint history:** eight documented sprints taking the surface from landing page to a 9-page app shell — auth and a 7-step onboarding wizard, home feed, story detail, briefing player, library, discover channels, live radio, search, profile/billing/voice/preferences/privacy, `/plans` with a **mock checkout routing to Paystack or Stripe**, breaking-news pill, WhatsApp share-clip modal, live headline ticker, **drag-reorder player queue with auto-advance**, a three-column desktop shell at 1200px+ with Now Playing and Up Next rails, a deep player with transcript, chapters, sleep timer and 0.75–2× playback speed.
- **Engineering and compliance details worth naming:** installable as a **PWA** (manifest plus `sw.js`, cache-first shell and network-first HTML), toast system, **keyboard shortcuts** (⌘K, space, arrows, j/k, ?) with a shortcuts modal, skeleton states and designed empty states, `500.html`, a **print stylesheet** for legal and story pages, press kit page, 44px touch targets, skip-link, `robots.txt` and `sitemap.xml`, and **NDPA-compliant privacy policy plus Terms governed by Nigerian law** written out in full. 30 seed stories including **Pidgin and Yorùbá body samples**.
- **Stack:** HTML, CSS, JavaScript (no framework, no build step), Service Worker API, Web App Manifest
- **Use for:** spec-driven prototyping, sprint planning and phased scope control, product design handoff to engineers, native-platform-first builds (Web Components-era vanilla skill rather than framework dependence), Nigerian data-protection compliance awareness, WCAG touch-target and keyboard requirements.
- **Caution:** it is a **prototype**. No backend, mock checkout, no real accounts. Say "prototyped the full app shell in build-free HTML, CSS and JavaScript so the product could be reviewed before engineering committed" — never "this is the live app".

### Narvo Platform
- **Tagline:** Developer portal and API playground for Narvo's NLP synthesis, translation, and text-to-speech APIs (NaaS), for newsrooms and enterprises.
- **Role:** Solo Designer & Developer · **10 weeks** · 2026 · In Progress
- **Problem:** Integrating African voice synthesis, regional translation, and automated editorial summarisation into third-party apps was complex and lacked accessible API infrastructure or tooling.
- **Solution:** Developer-centric portal with interactive code playground editors, secure client-side token authorisation via Supabase, developer analytics dashboards, and Mintlify-integrated API documentation. Canonical high-contrast Swiss Grid theme with neon-emerald dev accents.
- **Repo-verified engineering (2026-10-14):** **Next.js 16.2.4 with `output: "export"`** — a fully static build shipped to **Cloudflare Pages**, which is why auth is deliberately client-side: the README states plainly that static export means **no Next.js middleware**, so the session stays client-side until hosting changes. That is a real rendering-strategy trade-off, not an oversight, and it is worth citing as one. `pnpm` 9, Node 20, Tailwind CSS v4, Lucide icons, `@supabase/supabase-js` browser client for sign-in and sign-up. The playground posts real requests against `NEXT_PUBLIC_API_BASE_URL` with an `nrv_sk_*` key pasted in (responses stay simulated without it), which requires the API to send **CORS headers** for the portal origin. Docs live on a **Mintlify subdomain** (`docs.platform.narvo.news`), with `public/_redirects` sending `/docs` there on Pages and doc anchors aligned in `lib/docs.ts`. Design system committed as **Swiss Grid** tokens: 8px module, flat surfaces, zero radius, retained Narvo Signal/Void palette, in `styles/portal-css/tokens.css`. Same GitHub Actions gate as the consumer monorepo (lint, typecheck, build).
- **Stack:** Next.js 16 (static export), TypeScript, Supabase (client-side auth), Tailwind CSS v4, Lucide React, REST API, Mintlify, Cloudflare Pages (`_redirects`), pnpm, GitHub Actions
- **Live:** https://platform.narvo.news · **Repo (public, safe to link):** https://github.com/Narvo-Intelligence/narvo_platform
- **Use for:** B2B and developer tooling, API design and documentation, token auth, static-export architecture decisions, CDN/edge hosting with redirects, analytics dashboards, design systems.

### Narvo Intelligence
- **Tagline:** Corporate portal for the parent holding entity of the Narvo product family.
- **Role:** Solo Designer & Developer · **4 weeks** · 2026 · Completed
- **Problem:** Stakeholders needed a canonical, secure, highly performant corporate presence consolidating brand architecture, governance, and legal information without dynamic performance overhead.
- **Solution:** Lightweight static-export SPA, light-mode native institutional design, Cloudflare Pages Functions with Resend email, Plausible analytics, GlitchTip error tracking, **WCAG 2.1 AA** compliance.
- **Stack:** Next.js, TypeScript, Tailwind CSS v4, Cloudflare Pages, Resend, Plausible, GlitchTip, Lucide React
- **Live:** https://narvointelligence.xyz · **Repo: STILL PRIVATE — `github.com/Narvo-Intelligence/narvo_intelligence` returns 404 anonymously. Never link it.**
- **Use for:** accessibility compliance, performance, corporate/investor-relations sites, observability and analytics wiring.

#### Claim rules for the whole Narvo family

- **Phrasing that is safe and specific:** "an AI news pipeline that synthesises broadcast-style narratives, translates them into five languages including Yorùbá, Igbo, Hausa and Pidgin, generates the audio with a primary Nigerian-voice TTS provider and named fallbacks, and serves it through a PWA with offline playback." Every clause of that sentence is true of the public code.
- **Do not say:** that he "runs GCP infrastructure at scale", "owns the ML research", or that any of it has public user numbers. The claimable scope is *"designed and built this API and deployed it as a Docker image on Google Cloud Run"* — he has deployed on GCP; that is the tier.
- **Repo naming caution:** the shipping backend sits in a repo literally named `legacy_code_2`, and the original consumer prototype in `ajibolagenius/narvo` is archived. Use **"the Narvo API"** or **"the Narvo backend"** in prose; link the repo only when a reviewer wants to read code. Never let the folder name become the project name in the letter.
- **Private in the same org:** `narvo_intelligence` and `documentations` (the `current/` design, product and migration docs the public READMEs reference). Cite the live products, never those repos.
- **Live endpoints:** `api.narvo.news` appears in `narvo_platform`'s README as the *expected* API base. Do not present it as a working public endpoint unless it is verified live at that moment.

---

## Tier 3 — client sites and platforms

### Arsenal Nigeria Community (ANC)
- **Tagline:** (none on page) Full-stack community platform for Nigerian Arsenal fans.
- **Role:** Full-stack Engineer · **1 month** · 2026 · Type: dev
- **Problem:** Grassroots football fan communities across Nigeria rely on noisy WhatsApp groups, manual spreadsheets for member verification, repetitive giveaway forms, unverifiable raffle draws, and scattered meetup coordinates — with no unified tooling for moderation, scheduled engagement, or verified fan identity.
- **Solution:** Full-stack monorepo — Next.js 16 web app, Baileys-driven WhatsApp automation bot, Supabase (PostgreSQL & RLS) backend. Server-generated Fan Pass cards (@vercel/og), cron birthday greetings and AI news digests, audited raffle draws, state-by-state watch-party coordination with moderation tiers, fine-grained RBAC.
- **Stack:** Next.js, TypeScript, Supabase, Tailwind CSS v4, PostgreSQL, Zod, Resend, React, Baileys (WhatsApp Web API), Phosphor Icons, Claude AI, Sentry
- **Live / repo:** portfolio page only as of 2026-08-16 — https://ajibolagenius.vercel.app/projects/anc (no separate live product URL captured yet; do not invent one)
- **Use for:** PostgreSQL/RLS, RBAC, cron/async workflows, third-party messaging integrations, community ops tooling, observability (Sentry).

### JobHustles
- **Role:** Developer & Designer · **3 months** · 2026 · Client · Featured
- **Problem:** JobHustles operated locally with no dedicated online presence, limiting the founder's operational ambitions.
- **Solution:** A full career platform giving the business a digital footprint beyond offline activity.
- **Stack:** Next.js, Supabase, Phosphor Icons, Framer Motion, **Recharts**, Cloudflare, ESLint, TypeScript, Tailwind CSS, PWA
- **Live:** https://jobhustles.com.ng · **Repo: PRIVATE**
- **Use for:** platform builds, reporting/charts (Recharts), taking an offline business online.

### Sonasdigitals
- **Tagline:** Custom branding with the fastest turnaround.
- **Role:** Full-stack Engineer · **1 month** · 2026 · Client · Complete
- **Problem:** No online presence, reducing accessibility and flexibility for potential and returning customers.
- **Solution:** Bespoke site establishing their digital presence — service showcase, client contact, 24/7 accessibility, competitive positioning in a digital-first market.
- **Stack:** Supabase, Tailwind CSS, Next.js, Framer, GSAP, PWA, TypeScript
- **Live:** https://sonasdigitals.com · **Repo: PRIVATE**
- **Use for:** merchandise and print commerce, B2B branding workflows, order intake, small-business digitisation.

### Hotbite – Street Food
- **Role:** Solo Developer · **48 hours** · 2026 · Client · Featured
- **Problem:** Food websites are static and text-heavy, failing to translate the sensory excitement and bold aesthetic of street-food brands.
- **Solution:** Performance-oriented single-page Next.js app with custom marquee tickers, interactive galleries, Lenis kinetic scrolling, mobile-optimised responsive design.
- **Stack:** Next.js, React 19, TypeScript, Tailwind CSS v4, Lenis, Lucide React
- **Live:** https://hotbite-demo.vercel.app · **Repo (public):** https://github.com/ajibolagenius/hotbite
- **Use for:** ⭐ shipping something polished in **48 hours** — the sharpest proof of speed under deadline. Also F&B, hospitality, conversion-focused marketing sites.

---

## Tier 4 — side projects with real engineering depth

### ⭐ AfroGraph — Afrobeats Cultural & Collaboration Knowledge Graph
- **Tagline:** An interactive knowledge graph exploring the talent incubators (YBNL, Mavin, Starboy), sound architect producers, and multi-generational sample lineages powering the global Afrobeats phenomenon.
- **Role:** Creator & Full-Stack Graph Engineer · **1 week** · 2026 · Side · Live · Featured
- **Categories:** Graph Database, Interactive Knowledge Graph, Music Analytics
- **Problem:** Music ecosystems and cultural lineages are deeply interconnected networks. Relational databases struggle with variable-depth graph traversals, talent incubation blast radii, and recursive sample ancestry without expensive multi-table joins and slow recursive CTEs.
- **Solution:** Engineered a high-performance interactive graph application powered by CognoDB Cloud (openCypher over Bolt protocol via `neo4j-driver`) and Next.js 16 / D3.js. Features include shortest-path separation discovery, label talent incubation blast radius trees, multi-generational sample heritage explorer, producer hub centrality analytics, an interactive Cypher Query Studio with SQL benchmarks, and defensive Cypher security controls.
- **Stack:** CognoDB, openCypher, Next.js 16, React, TypeScript, D3.js, Tailwind CSS, neo4j-driver
- **Live:** https://afrograph.vercel.app · **Repo (public):** https://github.com/ajibolagenius/afrograph
- **Use for:** ⭐ Graph databases, knowledge graphs, openCypher / Neo4j / CognoDB, D3.js interactive network visualization, complex query optimization, music analytics / cultural tech.

### ⭐ Vertex — AI-Driven Learning Platform
- **Tagline:** An AI-driven learning platform that responds to plain-English questions with ranked cards, each linking directly to the precise second in a lesson video.
- **Role:** Implementing Engineer · **1 week** · 2026 · Side · Live
- **Categories (site):** the project page labels it a build-along; describe it as a shipped side project he built, and don't volunteer the tutorial origin unless asked directly.
- **Problem:** Course videos are hard to search. Learners guess which lesson covers a topic and scrub through long videos; keyword search misses, and AI chatbots fabricate lessons that do not exist.
- **Solution:** An offline ingestion pipeline turns videos into timestamped transcript segments. Sanity Context MCP lets an LLM generate GROQ queries against the real content, so results are grounded in the course itself and returned as ranked cards that deep-link to the exact second in a lesson.
- **Features:** AI semantic search with timestamp deep-linking; in-lesson interactive transcript panel; grounded Q&A with verified citations; offline-generated quizzes with streak tracking; learning paths and curated collections; progress tracking and playback resumption; PostHog analytics; PWA with offline support; "Signal" design system with light/dark themes.
- **Stack:** Next.js, React, TypeScript, Sanity, GROQ, Sanity Context MCP, Vercel AI SDK, OpenAI, Clerk, PostHog, Tailwind CSS, Portable Text, Zod
- **Live:** https://vertex-lms-app.vercel.app · **Repo (public):** https://github.com/ajibolagenius/vertex-lms
- **Use for:** headless CMS / Sanity / GROQ / structured content, MCP-grounded AI search (RAG without hallucination), Clerk auth, PostHog product analytics, video/learning products, PWA.
- **How to claim it:** plainly, as something he built and shipped — "built an AI-driven learning platform on Sanity and GROQ, where an LLM generates queries against the real course content so every answer deep-links to the exact second in a lesson." One week, live, public repo. Never call it client work or a commercial product; it is a side project, and that is all the qualification it needs.

### Mark_me — Bookmark Manager
- **Role:** Solo Designer & Developer · **4 months** · 2026 · Side
- **Problem:** Browser bookmark managers bury links in folder trees, lack visual previews and intelligent search/tagging, and make saving on the fly across devices hard.
- **Solution:** Monorepo with a Next.js 15 web app, a **Chrome MV3 extension**, and a shared neo-brutalist UI library. Neon Auth, Neon Postgres with Drizzle ORM, offline-first PWA sync via Serwist and IndexedDB, and an OpenRouter-powered AI assistant that summarises, tags, and answers questions about saved links.
- **Stack:** Next.js, TypeScript, PostgreSQL (Neon), Drizzle ORM, **tRPC**, Chrome + Firefox extensions, Tailwind CSS, Zustand, Serwist (PWA), OpenRouter
- **Live:** https://markme-app.vercel.app · **Repo (public):** https://github.com/ajibolagenius/mark_me
- **Use for:** browser extensions, tRPC, Drizzle/Neon, offline sync, AI assistants, monorepo + shared component libraries.

### AI-powered Football Analytics Platform ("The Culture AI Oracle")
- **Role:** Full-stack Engineer · **10 months** · 2026 · Side · In Progress
- **Solution:** End-to-end data science project that scrapes football match data, engineers advanced features (**Elo, Rolling xG, PPDA, Deep Completions**), and uses XGBoost classifiers to predict results and identify value bets. Glassmorphism Streamlit dashboard.
- **Stack:** Streamlit, Plotly, XGBoost, Scikit-Learn, Pandas, SQLAlchemy, PostgreSQL, RapidAPI, Football-Data.org, Understat, The Odds API, Tenacity, Claude, Supabase
- **Repo (public):** https://github.com/ajibolagenius/football-predictive-model
- **Use for:** data engineering and ETL pipelines, ML modelling, analytics dashboards, integrating multiple third-party data APIs, retry/resilience (Tenacity).

### Vibe Secure Me
- **Tagline:** Framework-agnostic security auditor skill for agentic AI assistants.
- **Role:** Solo Developer · **1 weekend** · 2026 · Side · Featured
- **Solution:** Equips AI coding assistants (Claude, Gemini, Codex, Cursor) to audit for vulnerabilities across "vibe-coded" apps and enterprise attack vectors spanning web, API, mobile, cloud, and AI platforms. Maps to **OWASP Top 10, API Security Top 10, Mobile Top 10, and LLM Applications Top 10**. Deep architectural review for broken access controls and business-logic flaws, with remediation guidance and secure-code examples.
- **Stack:** Claude, Antigravity, Codex, Terminal
- **Repo (public since 2026-08-12):** https://github.com/ajibolagenius/vibe-secure-me — safe to link. The repo has no description or topics set, so the portfolio page reads better; link the repo only when the JD wants to see code or security work.
- **Use for:** security-conscious roles, code review and quality processes, AI-assisted engineering workflows, automation.

### Rant / GoRant — Express Yourself Anonymously
- **Role:** Solo Designer & Developer · **1 year** · 2024 · Side · In Progress
- **Solution:** Anonymous gamified social platform — random friendly usernames, 12 mood categories, XP and level milestones, badges, leaderboards, weekly challenges, content moderation and sentiment analysis, real-time comments and likes, dynamic OG image generation.
- **Stack:** Next.js, TypeScript, Supabase, Tailwind CSS, Framer Motion, GSAP, Lenis, Sharp, Phosphor Icons
- **Live:** https://gorant.vercel.app · **Repos (public):** `gorant`, `rant` (open source)
- **Use for:** real-time features, gamification, content moderation and sentiment analysis, community products, open-source contribution.

### OlamideVerse
- **Role:** Solo Designer & Developer · **13 months** · 2025 · Side · Live
- **Solution:** Static-first Next.js 16 cultural archive organised around **six career eras** as a narrative spine, with albums, media, and stories hung off each era. Bespoke design system, GSAP ScrollTrigger scrollytelling, Zod-validated MDX/JSON content, planned Supabase community features (favorites, polls, comments).
- **Stack:** Next.js, TypeScript, Tailwind CSS, GSAP + ScrollTrigger, Supabase, MDX, PWA, JSON, React Leaflet, Zod
- **Live:** https://olamideverse.vercel.app · **Repo (public):** https://github.com/ajibolagenius/olamideverse
- **Use for:** editorial and storytelling builds, advanced scroll animation, content architecture and validation, design systems, cultural/media products.

### ⭐ Ajibola Portfolio & AI Concierge (Next.js 16 + Vercel AI SDK + Supabase)
- **Tagline:** High-performance personal CMS, AI concierge with tool calling, and technical publication platform.
- **Role:** Solo Designer & Developer · Continuous · Live · Featured
- **Problem:** Portfolios often act as static brochureware disconnected from live engineering activity, lacking modern interaction primitives, and failing to demonstrate claimed AI, design-system, or creative engineering capabilities.
- **Solution:** Engineered a dynamic personal platform featuring:
  - **AI Concierge & "Match My Job Description" Recruiter Mode**: Streaming assistant built with Vercel AI SDK (`ai`), rate-limited in-process API, RAG grounding across projects and experience, and client-rendered tool calls:
    - `matchJobDescription`: parses pasted job specs, returns structured match score %, key alignment points, and honest gaps.
    - `recommendProject`, `recommendNote`, `getLiveStatus`: interactive visual cards directly inside chat.
  - **Tactile Micro-Audio Engine**: Custom procedural Web Audio API synthesizer (`sound.ts`) producing crisp high-frequency clicks, pops, and chimes without external audio files; integrated with global `SoundToggle` state in navigation, and audio cues for theme switches, command palette triggers, and assistant events.
  - **Interactive System Architecture Visualizer**: Multi-tier SVG topology explorer (`architecture-visualizer.tsx`) visualizing distributed systems (e.g. Zora Market monorepo and AfroGraph Bolt/graph database architecture) with real-time animated packet simulation and node inspection.
  - **Notes Publication Platform**: Full-stack technical article CMS with dynamic per-slug OpenGraph cards, admin CMS editing, rich-text typography, and GEO/SEO architecture.
  - **Design System & Visual Engineering**: Modernized design tokens in `oklch()` color space with `@media (color-gamut: p3)` wide-gamut accents, asymmetric Bento grid with persistent `useSyncExternalStore` view switcher, and responsive `xl`/`2xl` scaling.
  - **App-Grade Interaction Primitives**: Global Command Palette (⌘K) with fuzzy indexing and recruiter match shortcut, native cross-route View Transitions API (`document.startViewTransition`), and live "Now" activity widget tracking Lagos WAT time and real-time GitHub commits.
  - **Naija Vintage Radio** (2026-09): cassette-deck audio player ("HIGH BIAS · C-90 · SIDE A") playing classic Nigerian tracks (e.g. King Sunny Ade's *Synchro System*, 1983) from local files with prebuffering, autoplay with unmount cleanup, per-track source citations (Apple Music), and a sidebar variant sharing one hook.
  - **Internationalisation — EN / YÓ:** language provider and switcher localising the UI into **Yoruba**.
  - **PostHog analytics** (2026-09): event capture across AI assistant, CV download, contact form, share buttons and project cards; owner visits flagged out of insights; PostHog hosts allow-listed in the CSP.
  - **Hardening:** CSP, error boundaries, WCAG skip link, smoke tests; a deliberate simplification pass removed dead code and duplication.
- **Stack:** Next.js 16, React 19, TypeScript, Supabase, Vercel AI SDK, Tailwind CSS 4, OKLCH, Three.js, PostHog, Phosphor Icons
- **Live:** https://ajibolagenius.vercel.app · **Repo (public):** https://github.com/ajibolagenius/ajibolagenius (the older `ajibola-portfolio` URL returns 404 — do not use it)
- **Use for:** ⭐ AI engineering, agentic UI / tool calling, RAG, Next.js 16 App Router architecture, modern CSS/OKLCH, View Transitions, design systems, performance, technical writing.

---

## Tier 5 — small, fast, and public

### Claude AI Theme for VS Code
Solo Developer · **1 weekend** · 2026. Three variants — Claude Light (#FAF9F5 warm off-white), Claude Dark (#1C1B18 warm charcoal), Claude Dusk (#2B2A27). Warm terracotta accents and a tuned syntax palette. Public: https://github.com/ajibolagenius/claude-ai-theme

### Narvo News Theme for VS Code
Solo Developer · **1 weekend** · 2026. Swiss-brutalist theme from the Narvo design system — four palettes (Nature, Sun, Dusk, Moon), sharp edges, mono-UI typography, 8pt spacing grid. Public: https://github.com/ajibolagenius/narvo-news-theme

### Webflow Portfolio (2022)
Solo Designer & Creator · **2022** · Live: https://ajibolagenius.webflow.io
- **Problem:** Needed a bespoke portfolio to showcase graphic design, branding, and commissioned client projects during his design career.
- **Solution:** Fully custom Webflow site featuring responsive layouts, custom typography and Google Fonts pairing, CSS/Webflow interactions (quote slider, masonry-style interactive project/blog tiles, full-screen contact overlay modal), and client intake forms.
- **Stack:** Webflow, HTML/CSS, Webflow CMS, JavaScript/jQuery, Google Fonts
- **Live:** https://ajibolagenius.webflow.io
- **Use for:** Webflow, No-Code / visual site builders, CMS-driven client sites, rapid landing page turnaround.

Both themes and the Webflow build are good proof of **design-system thinking, colour/contrast discipline, and visual page-building**, alongside custom engineering.

### Sandbox — https://ajibolagenius.vercel.app/sandbox
"Small experiments you can open and play with. Some are finished toys; others are still on the bench."
- **Mesh Lab** (`/sandbox/mesh-lab`) — an interactive 3D geometry and WebGL rendering playground.
  - **Role:** Solo Developer · 2026 · Sandbox Toy · Live
  - **Features:** Four parametric buffer geometries (Torus Knot, Icosahedron, Dodecahedron, Octahedron), three rendering styles (shaded material, wireframe, particle points), wireframe overlay toggle, variable rotation speed, pointer-drag with inertial damping, particle count telemetry, and automatic reduced-motion suspension.
  - **Stack:** Three.js, WebGL, React 19, TypeScript, Tailwind CSS
  - **Live:** https://ajibolagenius.vercel.app/sandbox/mesh-lab
  - **Use for:** ⭐ Three.js, WebGL, creative development, 3D math and geometry, interactive canvas physics, reduced-motion accessibility. Closes the credibility gap for the Bruno Simon Three.js certification on CV.
- **Color Lab** (`/sandbox/color-lab`) — a contrast playground: drag or type hex values, real-time **WCAG contrast ratio** calculation with pass/fail status, Site/Invert/Accent/Muted modes. Described as "a tiny scratch space for testing weird CSS grid layouts and micro-animations." Useful evidence for accessibility literacy.

---

## Public repos not featured on the portfolio

Worth mentioning only when directly relevant:

- **lagos-spots** — HTML. Full-stack app for exploring Lagos attractions, restaurants, and landmarks. Another Nigeria-first build; light on depth, cite only if the role is local-discovery or maps adjacent.
- **lagos-spots-web** — newer companion repo to lagos-spots, no description yet. Same rule.
- **EduPoint** — programme repository for the EduPoint Professional Skills Development Programme at Trinity University, Yaba (Faculty of Science and Technology). Public teaching evidence; safe to link for training/mentoring roles.
- **bemahub-swe-assessment** — his BemaHub Software Engineer hiring assessment. **Do not cite** — it is an employer's screening exercise, and Bema evidence comes from the employment itself.
- **massweddings** — TypeScript. Data mappings of mass weddings in Nigeria over the past 10 years. Data-collection/mapping side work.
- **corpsmart** — TypeScript. "Nigeria's most trusted marketplace exclusively for NYSC corps members." Another Nigerian marketplace build.
- **narvo** — JavaScript, archived. The original mobile-first, voice-first news platform that became Narvo News. Superseded by the public `Narvo-Intelligence` repos; cite it only as the origin of the idea.
- **Narvo-Intelligence org, public since 2026-10-14** — `narvo_news`, `narvo_platform`, `legacy_code_2` (the Narvo API), `narvo-app-proto`. All safe to link; full dossiers in Tier 2. His GitHub company field reads `@narvo_news`.
- **3d_todo_tobamsgroup** — TypeScript, MIT. Next.js + React Three Fiber 3D to-do app with progress visualisation.
- **lecture_notes** / **lecture_notes_old** — TypeScript. Teaching material from Deejoft and APTECH — concrete evidence of the tutoring and documentation claims.
- **jsm_gsap_cp**, **mojito_gsap** — GSAP animation practice.
- **level-29**, **barnabs**, **simple-blog-enhanced**, **SimpleGameWindow**, **React-Project1–13** — early learning repos. Do not cite these in applications; they date from Jan–Feb 2025 and undersell him.
- Forks: `awesome-python`, `learn-vanilla-js`, `ML-For-Beginners`, `Amazing-Python-Scripts`, `yarngpt`.

## Cross-cutting patterns worth naming in an application

- **A shipped app-store product:** Zora Market on the Apple App Store, with a release history (1.0.14). Passing review and shipping updates is a different skill from building a demo, and it is the rarest thing in this portfolio. Lead with it whenever the role is remotely mobile- or product-adjacent.
- **Code a recruiter can now read:** the Narvo API, the consumer monorepo, the B2B portal and the app prototype are **public repos** (since 2026-10-14). For backend, Python, API-design or AI-infrastructure roles, name the repo, not just the product — "the FastAPI service is public if you would like to read it" is a stronger close than any adjective, because it invites the check instead of surviving it.
- **Resilience by design, not as a buzzword:** the Narvo API declares a **primary and a fallback for every model provider** (Gemini then Groq for narrative and translation; YarnGPT then Google Cloud TTS then OpenAI for speech), retries ingestion with `tenacity`, keeps a provider-status service for health, and serves a 429 from a rate-limit middleware keyed on user id before IP. That is a coherent reliability story built from shipped code, and each clause has a file behind it.
- **Contract discipline in the API:** one standardised JSON error envelope carrying `code`, `status` and `request_id`, applied to `HTTPException`, framework 404/405s and unhandled errors alike; request-ID middleware with per-request latency logging as structured JSON for container logs; a versioned OpenAPI surface with a custom-themed Swagger UI and a version-bump script. Useful whenever the brief says "clean", "consistent", "well-documented" or "production-grade" APIs.
- **Asynchronous and scheduled work he can actually name:** **Upstash QStash** cron triggers for the 5am Morning Briefing and weekly TTS-cache cleanup, with **inbound request-signature verification and current-plus-next key slots so rotation causes no downtime**, then fan-out to web push via `pywebpush` with VAPID keys. This is the concrete evidence behind the otherwise generic "asynchronous cron workflows" line; still no Kafka, RabbitMQ, Service Bus or Transactional Outbox.
- **Server-side data modelling with a security default:** Supabase Postgres migrations including an explicit RLS policy file, user-scoped tables, JSONB per-language translations and audio, source-reputation and push-subscription tables, and a written convention that **RLS is mandatory on every new table** with `auth.uid() = user_id`. Pair with ANC's RLS and RBAC for a "thinks about permissions first" argument.
- **Quality gates across two ecosystems:** pytest and pytest-asyncio over **35 test modules** plus `mypy`, `pyright`, `black`, `isort` and `flake8` on the Python side; ESLint, `tsc --noEmit` and build in **GitHub Actions with concurrency cancellation** on both Next.js repos; Vitest and Playwright at Bema. The pattern is "no repo merges without a gate", and it is now provable from public CI files.
- **Nigeria-first engineering:** Paystack, Naira currency systems, 3G-optimised offline caching, five-language localisation, NYSC and diaspora marketplaces, **NDPA-compliant privacy policy and Terms governed by Nigerian law**. He builds for real Nigerian constraints, not just for a global template.
- **Agentic AI & Tool Calling in production:** The portfolio AI concierge isn't a wrapper or chatbot iframe — it's an integrated streaming agent built on Vercel AI SDK with custom client-rendered tool calling (`recommendProject`, `recommendNote`, `getLiveStatus`), in-process rate-limiting, and dynamic Supabase context grounding.
- **Ship the spec before the stack:** the Narvo app prototype proves he will take a product through eight documented sprints in build-free HTML, CSS and JavaScript, with a service worker, keyboard shortcuts, empty states, a 500 page, print stylesheets and legal pages, before any framework budget is spent. Strong for early-stage and founder-led teams, and for roles that name prototyping, spec work or design engineering.
- **Modern CSS & wide-gamut design systems:** OKLCH perceptually uniform color tokens, Display-P3 wide-gamut media queries, asymmetric Bento grid architecture with persistent `useSyncExternalStore` view switcher, responsive `xl`/`2xl` scaling, and native cross-route View Transitions API (`document.startViewTransition`).
- **Design tokens as shared contracts:** one `b2c-tokens.css` across two consumer apps and a committed Swiss Grid token file (8px module, flat surfaces, zero radius) on the B2B portal — the design-system habit carried into repository structure, not just Figma files.
- **End-to-end ownership:** credited "Solo Designer & Developer" or "Solo Developer" on **10 of the 23** projects — design, build, deploy, and maintain.
- **Range of tempo:** 24 hours (Branda V2), 48 hours (Hotbite) to 18 months (Narvo News). Pick whichever the JD implies it values.
- **Production payments across two gateways:** Paystack and Stripe, plus a custom wallet with automated escrow.
- **Design systems as a habit:** Swiss Grid, neo-brutalist, Swiss-brutalist, 8pt grids, WCAG AA — carried from the design career into engineering.
