---
name: jd
description: >
  Turn a job description into a tailored job application message for Ajibola Akelebe. Use whenever
  the user pastes a job posting, job ad, JD, role brief, or job link and wants an application email,
  cover letter, cover note, recruiter DM, referral message, or "why I'm a fit" write-up. Also use
  for tailoring an existing application to a specific role, drafting a follow-up to one, or checking
  how well he matches a role. Grounds every claim in his real CV, portfolio, and GitHub, and always
  includes his three links.
---

# /jd — Job description to application message

Turn any job description into a targeted application message, grounded in real evidence from
Ajibola Akelebe's CV, portfolio, and GitHub. Never invent experience.

## Canonical install — one copy, everywhere

**Source of truth (edit only here):** `~/.agents/skills/jd/`. Every other agent resolves to it by
symlink — never a duplicated tree. A second full copy means a stale fork: delete it, restore the link.

| Agent | Path |
|---|---|
| Claude Code | `~/.claude/skills/jd` → `../../.agents/skills/jd` |
| Cursor | `~/.cursor/skills/jd` → `../../.agents/skills/jd` |
| Codex | `~/.codex/skills/jd` → `../../.agents/skills/jd` |

| File | Read it when |
|---|---|
| `profile.md` | **Always.** Identity, contact, experience, skills, the requirement→evidence mapping cheatsheet, claim tiers, never-claim list. |
| `projects.md` | Whenever project depth is needed — role, duration, stack, problem/solution, features, live links, per-project cautions. |

## Inputs

The JD may arrive as text pasted after `/jd`, a URL, a screenshot, or earlier in the conversation.
Fetch URLs when given one. LinkedIn, Indeed, and most job boards block scraping — if the fetch fails,
ask for the pasted text rather than guessing at the role. No JD present? Ask for one. Never produce
a generic letter.

## Step 1 — Load the evidence

Read `profile.md`, and `projects.md` too unless the JD is trivial.

Evidence verified **2026-10-08**; voice, length and gap rules calibrated **2026-10-14** from a letter
he sent (Klooqi Frontend Tech Lead). **A letter he actually sent is better evidence of his preference
than any draft he edited.** Refresh when the snapshot looks stale, he says something changed, or the
role is high-stakes.

**Cheap change-detection first.** `curl` the sitemap and compare `<loc>`/`<lastmod>` against
`projects.md`; check the GitHub API's `pushed_at` and repo count. Two calls reveal what moved — fetch
only that. His site changes often, so verify rather than assume. WebFetch caches 15 minutes per URL;
add a throwaway query param (`?fresh=1`) to re-check a page you just read.

Full refresh sources:

- https://ajibolagenius.vercel.app/cv
- https://ajibolagenius.vercel.app/projects (index; per-project pages at `/projects/<slug>`)
- https://ajibolagenius.vercel.app/sitemap.xml (fastest way to spot new or renamed projects)
- https://api.github.com/users/ajibolagenius/repos?per_page=100&sort=pushed

If a fetch contradicts the cache, update the file, note the date, and say what changed.

## Step 2 — Read the JD like a hiring manager

Extract, in this order of weight:

1. **Required qualifications** — the gate. Each needs an answer or a deliberate omission.
2. **Preferred / "will be an advantage" skills** — where the application is won. They reveal what the company actually struggles with.
3. **Key responsibilities** — the day job. Map projects to these, not to job titles.
4. **Personal attributes and KPIs** — how performance will be judged. Mirror this language once or twice, naturally; never parrot the list.
5. **Company, industry, and stage** — a fashion brand, a fintech, and an agency need different proof from the same résumé.

**Pick the two or three strongest pieces of evidence as the spine.** Proving three things well beats
listing ten. For a **senior or lead** role, expand to four to six labeled blocks — but only when each
block answers a *different* requirement in the JD. Padding to hit a block count is worse than three
strong blocks.

## Step 3 — Match evidence to the role

- Start from the **mapping cheatsheet** in `profile.md`, then verify the detail in `projects.md` before writing about a project.
- **Check whether the store apps earn a mention.** The Zora Market app is live on the Apple App Store and Google Play — the strongest single item in the portfolio and the rarest among Nigerian applicants. Full facts, phrasing rules, and the fourth link line are in `profile.md` → "Headline credential".
- Prefer **shipped projects over job titles**, and **domain-adjacent over impressive-but-unrelated**. NEGOtivity (apparel storefront) beats a bigger fintech build when applying to a fashion brand.
- Prefer **specifics only he could write** — the Naira-focused currency system, the Empire Wallet with automated escrow, one Turborepo serving an Expo app and four web surfaces, IndexedDB caching tuned for 3G, five-language TTS. "Passionate developer" is noise.
- **Quote the site's own numbers** — role titles, durations, stacks. Don't inflate them; never invent a metric the site doesn't state.
- **Two things he routinely cuts from the final letter (observed 2026-10-14).** Draft them in, then flag them: (a) **any number belonging to a current employer** — Bema's test counts, traffic, revenue, team size; (b) **build durations** in lead/senior letters ("solo in 48 hours"), unless the JD explicitly rewards speed. Stack versions and store facts always stay.
- Lead with the **industry match** when one exists; with the **hardest technical requirement** when one doesn't.
- Turn the **design career and teaching work** into role-specific arguments, not biography. Design → customer experience, brand judgment, design-to-code fidelity. Teaching → explaining trade-offs to non-technical stakeholders, documentation discipline.
- **Match tempo** to what the JD values: Branda V2 (24 hours) or Hotbite (48 hours) for speed under deadline; Narvo News (18 months) or OlamideVerse (13 months) for long-haul ownership.
- **Nigeria-first engineering** is a differentiator for Nigerian and Africa-focused employers: Paystack, Naira handling, 3G optimisation, local-language localisation. Say it plainly.
- **AI tooling, interactive/tactile-sound engineering, headless CMS, testing, container deployment** all have dedicated cheatsheet rows — use the row, don't re-derive it.

### Framing cautions — these get him caught out if written wrong

- **Branda V2** carries multi-market, technical-SEO and rendering-strategy evidence, and it was a **screening task**. Never "built for Branda", never imply Branda uses it, never imply real payments (checkout is mocked). Say "built a four-market storefront in 24 hours".
- **Vertex** carries Sanity / GROQ / MCP / Clerk / PostHog. Claim it plainly as a **shipped side project** — built in a week, live, public repo. Don't hedge it, and never call it client work.
- **Bema Integrated Services** carries Vitest, Playwright, Coolify, Trello and Plane. Cite it as **employment engineering**, never as a portfolio project — BemaHub and Bema Pages are the employer's systems.
- **Fidia** is "Co-Founder & Brand/Visual Designer", never "Design Lead", and never link getfidia.com (dead since the 2023 closure). Details in `profile.md`.
- Where the JD names a tool he hasn't used, do **not** claim it. Use the substitution table at the end of `profile.md`: name the transferable thing he shipped and let the parallel do the work.

### Link safety — do not skip this

**Eight** project repos are private or org-restricted and return 404 to anyone not signed in: `zora`,
`hekaiq`, `negotivity`, `sonasdigital`, `Job-Hustles-Recruiting-Platform`, and the three
`Narvo-Intelligence/*` repos. A recruiter sent to a 404 is worse than one sent nothing. Cite the
**live product URL**, the **App Store listing**, or the portfolio project page instead. Public repos
safe to link, and the full policy, are listed in `profile.md`.

The projects index is **`/projects`**, not `/work`. The portfolio's own source is
`ajibolagenius/ajibolagenius` — `ajibola-portfolio` 404s. Verify any project link against
`projects.md` before writing it.

## Step 4 — Write the message

Produce **two versions** unless told otherwise.

**A. Primary email** — 250–500 words. Lead and senior applications run long: he sends every evidence
block the JD asks for, then cuts numbers, not substance.

- **To** and **Subject** lines. If the posting dictates a subject, reproduce it **verbatim** — it's often an inbox filter.
- One-sentence opener naming the role and the single most relevant thing about him. Never "I am writing to apply for the position advertised."
- **Labeled evidence blocks** (count per Step 2): each starts with a short label mirroring the JD's own responsibility wording, then a colon, then 2–4 sentences of proof. His Klooqi labels: "Mobile architecture and release lifecycle", "Checkout journeys", "Design systems, not component collections", "Frontend craft under real-world constraints", "Leading a small team". Label-first beats prose because a skimmer gets the map before the detail.
- **One honest-gap paragraph**, near the end, from the template below. He kept it in the sent letter; it is not optional.
- Availability and logistics: location, on-site vs remote, start date.
- The links, each on its own line.
- Sign-off block: name, title, email, phone, LinkedIn.

**B. Short version** — 100–150 words for WhatsApp, a LinkedIn DM, a recruiter reply, or an
application form's free-text box. Same evidence, stripped to claims and links.

### The gap paragraph — the template he sends

Name the missing platform, name what he has actually deployed or built instead, assert that the
principles transfer in one concrete line, close on transparency. Verified 2026-10-14:

> Regarding areas where I do not yet have direct experience: **the platform(s) in the brief he cannot
> claim**. My backend work has focused on Node.js and Python, and I have deployed on GCP, Vercel,
> Cloudflare Workers, and Docker containers on AWS via Coolify. The underlying architectural
> principles are transferable: I have designed asynchronous cron workflows, real-time event flows,
> and queue-backed messaging patterns. However, I would need to learn the specific platforms, and I
> prefer to be transparent about that from the outset.

- "I do not yet have direct experience" — forward-looking. No apology, no "unfortunately", no promise to learn it fast.
- "queue-backed messaging patterns" is approved generic phrasing for event-driven and queue briefs. **Never name a pattern he hasn't shipped** (Transactional Outbox, Service Bus, Kafka, RabbitMQ).
- In the Klooqi letter he named **Azure only** and left **.NET unmentioned**, though the JD required both. That is his call, not a licence to hide a gate: list every unclaimed required skill in Confirm-before-sending and ask which to name. **Default to naming all of them.**

## Voice and register

Two registers, and they are not the same. The rules below govern **chat about the draft**; the letter
itself is formal plain prose. Read the draft back and ask: would a person say this out loud to someone
they respect? If not, cut it.

**Drafting principles**

- **Direct, not decorated.** Say the thing, then stop. No throat-clearing, no closing flourish restating the opener.
- **Confident, not boastful.** State what he built and let the fact carry the weight. Don't editorialize on top of it ("which is a huge achievement"). Adjectives stacked on an achievement read as insecure.
- **No sugarcoating.** Skip softeners — "I would love the opportunity to", "I truly believe", "I am confident that I". Say: "I built X. It does Y." If a claim is thin, say less about it rather than dressing it up.
- **Short sentences, varied rhythm.** A string of same-length sentences reads as generated.
- **Specific over generic.** A number, a stack, a timeframe beats an adjective. "Shipped in 48 hours" beats "fast-paced environment."
- **One idea per sentence.** No stacked clauses proving three things at once.

**The letter's register (from his 2026-10-14 edits — every one moved in this direction)**

- **Expand contractions:** "I am a Lagos-based Full Stack Engineer", "I have delivered". (One "I've" survived his edit; not permission.)
- **No em-dashes.** He rewrote every one into a colon or a comma. Colon-led detail lists: "a single Expo codebase: Expo SDK 55, Expo Router, NativeWind."
- **Spell out acronyms and compounds:** "over-the-air updates", not "OTA"; "end-to-end journeys". Stack versions stay as written (Expo SDK 55, React 19).
- **Plain, formal vocabulary.** "component collections" not "component piles"; "where checkout processes can lose revenue and customers" not "where checkout leaks money". Cut casual idioms and metaphors; keep technical nouns exact.
- **"Independently" instead of "solo."**
- **Full-sentence courtesies are welcome** — "I prefer to be transparent about that from the outset", "Kind regards". Courteous, not deferential.

**Banned outright** — none survive a first draft: "I am excited to apply", "passionate about", "proven
track record", "results-driven", "leverage", "synergy", "I believe I would be a great fit", "dynamic",
"cutting-edge", "seamlessly", "utilize", "in today's fast-paced world", "I am confident that", "look
forward to the opportunity to discuss further" — and any sentence that would survive unchanged in an
application to a different company.

## ATS compliance — it clears a parser before a person reads it

- **Plain text structure.** No tables, columns, text boxes, images, icons, headers or footers in the body. Strip markdown before it goes into a form field or plain-text client (bold becomes nothing; a bullet becomes a hyphen).
- **Standard section order.** Subject/opener → fit → evidence → gap → logistics → links → sign-off. Don't bury the role title or strongest match three lines down.
- **Mirror the JD's keywords once, verbatim.** If it says "REST APIs", write "REST APIs", not "RESTful services" — matching is literal, and a correct synonym can still miss the filter.
- **Spell out the posting's role title at least once**, exactly as written; some parsers gate on an exact match.
- **Links as plain URLs on their own line**, never anchor text ("click here", "my portfolio") — parsers strip the href and keep the anchor.
- **Standard punctuation only** — no bullet glyphs (•, ▸), no emoji, plain hyphen for lists, and no em-dashes (see the letter register above).
- Fonts and design elements apply to the CV attachment, not this output — but if the posting demands a specific format (e.g. ".docx not PDF"), flag it in Confirm-before-sending; some parsers still fail on PDF.

## Step 5 — Flag, don't assume

End with a short **"Confirm before sending"** list covering every assumption:

- **Location and work mode** — he is in **Lagos**. Flag any assumption about relocation, commute, or on-site work.
- **Salary** — omit it when the posting states a figure. If a form demands an expectation, ask him for a number; never invent one, and never negotiate against himself in a first message.
- **Attachments** — restate what the posting asked for (CV, portfolio, GitHub, cover letter, samples) and whether the draft references something he must actually attach.
- **Every required skill he cannot claim** — list them all and ask which to name in the gap paragraph. A silent gap discovered in the interview is worse than the awkward paragraph now.
- **Employer-internal numbers and build durations** — draft them in, flag them for deletion; his default is to cut them.
- **Sensitive verticals** — Nego is an adult-adjacent companionship marketplace. Lead with the technical substance (wallet, escrow, Paystack, tiered access control) and flag the vertical so he can decide. For conservative or family-brand employers, prefer Zora as the payments example.
- **Branda V2 and Fidia framing** — screening build, not client work; "Co-Founder & Brand/Visual Designer", no dead links.
- **Anything you softened** because the evidence was thin, so he can strengthen it if you were wrong.
- **Standing commitments** — the EduPoint programme runs Thursdays onsite at Trinity University, Lagos. Disclose plainly if the JD asks about availability; never state the sessional fee or terms.

Optionally close with **one** portfolio observation — a gap this posting exposed that's worth fixing
before a recruiter clicks through. Only when genuinely useful; skip rather than invent.

## Hard rules

- **Never fabricate.** No invented metrics, employers, dates, certifications, or tools. If it isn't in `profile.md`, `projects.md`, or a fresh fetch, it doesn't go in the message.
- **Never link a private repo.** See Link safety.
- **Always include** portfolio, CV, and GitHub in the primary email; at least portfolio and GitHub in the short version. App Store link for mobile, e-commerce and consumer-product roles.
- **Every draft clears both checks** — Voice and register (no banned phrases, no boasting, no filler, formal letter register) and ATS compliance (plain structure, verbatim keywords, plain URLs) — before it is shown to him.
- Output drafts as copy-pasteable markdown in the reply. Only write files when asked.
- **Never send anything anywhere.** Drafting only — he sends it.
