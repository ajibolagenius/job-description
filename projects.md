# Project dossier — Ajibola Akelebe

Every project on https://ajibolagenius.vercel.app/projects, verified 2026-09-04.
Site's own database holds **23 projects & sandbox toys** (21 listed on `/projects` + Color Lab and Mesh Lab on `/sandbox`). Roles, durations, and stacks
are as stated on each project page — quote them, don't embellish them.

⚠️ **Repos marked PRIVATE return 404 publicly.** Never link them in an application. Cite the live
URL or the portfolio project page instead.

**Changed 2026-09-04:** Added *Mesh Lab* 3D experiment (`/sandbox/mesh-lab`), *AI Assistant* with tool-calling & RAG over Supabase, *Notes & Writing* platform (`/notes`), global *Command Palette (⌘K)*, native *View Transitions API*, and *OKLCH / P3 wide-gamut* design system.
Fidia page on site labels the role "Co-founder & Design Lead" —
applications must still use **"Co-Founder & Brand/Visual Designer"** per the Medium post-mortem
(see `profile.md`); do not elevate the claim to Design Lead just because the portfolio page does.

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

### Narvo News
- **Tagline:** Consumer B2C surface for Narvo, transforming daily news feeds into localized, high-quality audio briefings using advanced speech synthesis and AI narrative alignment.
- **Role:** Full-stack Engineer · **18 months** · 2026 · In Progress
- **Problem:** African news platforms are text-heavy, ignore local dialects and language barriers, and add friction through data constraints and weak reporting transparency.
- **Solution:** Multilingual audio-first PWA with AI translation across **five languages (Yorùbá, Igbo, Hausa, Pidgin, English)**, high-quality TTS, thumb-first mobile interface, offline access, and a proprietary **Provenance Tag** system tracking AI consensus for source transparency.
- **Stack:** Next.js, TypeScript, FastAPI, Tailwind CSS, Zod, PWA, Speech Synthesis, Phosphor Icons, YarnGPT (TTS), Gemini, Groq
- **Live:** https://narvo.news · **Repo: PRIVATE (org)**
- **Use for:** AI/LLM integration, Python backends (FastAPI), accessibility, localisation, emerging-market product thinking, long-term ownership.

### Narvo Platform
- **Tagline:** Developer portal and API playground for Narvo's NLP synthesis, translation, and text-to-speech APIs (NaaS), for newsrooms and enterprises.
- **Role:** Solo Designer & Developer · **10 weeks** · 2026 · In Progress
- **Problem:** Integrating African voice synthesis, regional translation, and automated editorial summarisation into third-party apps was complex and lacked accessible API infrastructure or tooling.
- **Solution:** Developer-centric portal with interactive code playground editors, secure client-side token authorisation via Supabase, developer analytics dashboards, and Mintlify-integrated API documentation. Canonical high-contrast Swiss Grid theme with neon-emerald dev accents.
- **Stack:** Next.js, TypeScript, Supabase, Tailwind CSS, Lucide React, REST API, Mintlify
- **Live:** https://platform.narvo.news · **Repo: PRIVATE (org)**
- **Use for:** B2B and developer tooling, API design and documentation, token auth, analytics dashboards, design systems.

### Narvo Intelligence
- **Tagline:** Corporate portal for the parent holding entity of the Narvo product family.
- **Role:** Solo Designer & Developer · **4 weeks** · 2026 · Completed
- **Problem:** Stakeholders needed a canonical, secure, highly performant corporate presence consolidating brand architecture, governance, and legal information without dynamic performance overhead.
- **Solution:** Lightweight static-export SPA, light-mode native institutional design, Cloudflare Pages Functions with Resend email, Plausible analytics, GlitchTip error tracking, **WCAG 2.1 AA** compliance.
- **Stack:** Next.js, TypeScript, Tailwind CSS v4, Cloudflare Pages, Resend, Plausible, GlitchTip, Lucide React
- **Live:** https://narvointelligence.xyz · **Repo: PRIVATE (org)**
- **Use for:** accessibility compliance, performance, corporate/investor-relations sites, observability and analytics wiring.

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
  - **AI Concierge & Tool Calling**: Streaming assistant built with Vercel AI SDK (`ai`), rate-limited in-process API, RAG grounding across projects and experience, and client-rendered tool calls (`recommendProject`, `recommendNote`, `getLiveStatus`) showcasing interactive UI components directly in chat.
  - **Notes Publication Platform**: Full-stack technical article CMS with dynamic per-slug OpenGraph cards, admin CMS editing, rich-text typography, and GEO/SEO architecture.
  - **Design System & Visual Engineering**: Modernized design tokens in `oklch()` color space with `@media (color-gamut: p3)` wide-gamut accents, asymmetric Bento grid with persistent `useSyncExternalStore` view switcher, and responsive `xl`/`2xl` scaling.
  - **App-Grade Interaction Primitives**: Global Command Palette (⌘K) with fuzzy indexing, native cross-route View Transitions API (`document.startViewTransition`), and live "Now" activity widget tracking Lagos WAT time and real-time GitHub commits.
- **Stack:** Next.js 16, React 19, TypeScript, Supabase, Vercel AI SDK, Tailwind CSS 4, OKLCH, Three.js, Phosphor Icons
- **Live:** https://ajibolagenius.vercel.app · **Repo:** https://github.com/ajibolagenius/ajibola-portfolio
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

- **corpsmart** — TypeScript. "Nigeria's most trusted marketplace exclusively for NYSC corps members." Another Nigerian marketplace build.
- **narvo** — JavaScript, archived. The original mobile-first, voice-first news platform that became Narvo News.
- **3d_todo_tobamsgroup** — TypeScript, MIT. Next.js + React Three Fiber 3D to-do app with progress visualisation.
- **lecture_notes** / **lecture_notes_old** — TypeScript. Teaching material from Deejoft and APTECH — concrete evidence of the tutoring and documentation claims.
- **jsm_gsap_cp**, **mojito_gsap** — GSAP animation practice.
- **level-29**, **barnabs**, **simple-blog-enhanced**, **SimpleGameWindow**, **React-Project1–13** — early learning repos. Do not cite these in applications; they date from Jan–Feb 2025 and undersell him.
- Forks: `awesome-python`, `learn-vanilla-js`, `ML-For-Beginners`, `Amazing-Python-Scripts`, `yarngpt`.

## Cross-cutting patterns worth naming in an application

- **A shipped app-store product:** Zora Market on the Apple App Store, with a release history (1.0.14). Passing review and shipping updates is a different skill from building a demo, and it is the rarest thing in this portfolio. Lead with it whenever the role is remotely mobile- or product-adjacent.
- **Nigeria-first engineering:** Paystack, Naira currency systems, 3G-optimised offline caching, five-language localisation, NYSC and diaspora marketplaces. He builds for real Nigerian constraints, not just for a global template.
- **Agentic AI & Tool Calling in production:** The portfolio AI concierge isn't a wrapper or chatbot iframe — it's an integrated streaming agent built on Vercel AI SDK with custom client-rendered tool calling (`recommendProject`, `recommendNote`, `getLiveStatus`), in-process rate-limiting, and dynamic Supabase context grounding.
- **Modern CSS & wide-gamut design systems:** OKLCH perceptually uniform color tokens, Display-P3 wide-gamut media queries, asymmetric Bento grid architecture with persistent `useSyncExternalStore` view switcher, responsive `xl`/`2xl` scaling, and native cross-route View Transitions API (`document.startViewTransition`).
- **End-to-end ownership:** credited "Solo Designer & Developer" or "Solo Developer" on **9 of the 18** projects — design, build, deploy, and maintain.
- **Range of tempo:** 48 hours (Hotbite) to 18 months (Narvo News). Pick whichever the JD implies it values.
- **Production payments across two gateways:** Paystack and Stripe, plus a custom wallet with automated escrow.
- **Design systems as a habit:** Swiss Grid, neo-brutalist, Swiss-brutalist, 8pt grids, WCAG AA — carried from the design career into engineering.
