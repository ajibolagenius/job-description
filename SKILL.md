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

## Canonical install — keep every agent on the same copy

**Source of truth (edit only here):** `~/.agents/skills/jd/`

All agents must resolve to that directory via symlink — never a duplicated tree:

| Agent | Path |
|---|---|
| Canonical | `~/.agents/skills/jd/` |
| Claude Code | `~/.claude/skills/jd` → `../../.agents/skills/jd` |
| Cursor | `~/.cursor/skills/jd` → `../../.agents/skills/jd` |
| Codex | `~/.codex/skills/jd` → `../../.agents/skills/jd` |

Update the canonical folder once; every agent picks up the change. A second full copy anywhere
means a stale fork — delete it and restore the symlink.

## Files in this skill

| File | Read it when |
|---|---|
| `profile.md` | **Always.** Identity, contact, CV, skills, education, certifications, the requirement→evidence mapping cheatsheet, and the never-claim list. |
| `projects.md` | Whenever you need project depth — role, duration, stack, problem/solution, features, live links. All projects, tiered by application value. |

## Inputs

The JD may arrive as: text pasted after `/jd`, a URL, a screenshot, or earlier in the conversation.
Fetch URLs when given one. LinkedIn, Indeed, and most job boards block scraping — if the fetch
fails, ask for the pasted text rather than guessing at the role.

No JD present? Ask for one. Never produce a generic letter.

## Step 1 — Load the evidence

Read `profile.md`. Read `projects.md` too unless the JD is trivial.

Both were last verified on **2026-08-16** (sitemap + GitHub change-detection; ANC and Fidia
project pages added). Refresh when the snapshot looks stale, the user says something changed, or
the role is high-stakes.

**Cheap change-detection first.** `curl` the sitemap and compare `<loc>`/`<lastmod>` against
`projects.md`; check the GitHub API's `pushed_at` and repo count. Two calls reveal what moved —
fetch only that. His site changes often, so verify rather than assume. WebFetch caches 15 minutes
per URL; add a throwaway query param (`?fresh=1`) to re-check a page you just read.

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

Then pick the **two or three strongest pieces of evidence** and build around them. Proving three
things well beats listing ten.

## Step 3 — Match evidence to the role

- Use the **mapping cheatsheet** in `profile.md` as the starting point, then verify the detail in `projects.md` before writing about a project.
- **Check whether the store apps earn a mention.** Zora Market is live on the **Apple App Store** (v1.0.14, released 2026-04-30) and **Google Play** (per user confirmation 2026-08-14). For any mobile, consumer-product, e-commerce, or "demonstrable experience" requirement, this is the strongest evidence available — a product that passed review on both stores and ships OTA updates. Add the App Store URL as a fourth link line for those roles (Play URL optional when space allows). Skip only when the role is genuinely unrelated. Phrase him as the **engineer**, never the publisher (it ships under ZORA AFRICA LIMITED), and never imply downloads or ratings — there are none yet.
- Prefer **shipped projects over job titles**, and **domain-adjacent over impressive-but-unrelated**. NEGOtivity (apparel storefront) beats a bigger fintech build when applying to a fashion brand.
- Prefer **specifics only he could write** — the Naira-focused currency system, the Empire Wallet with automated escrow, one Turborepo serving an Expo app and four web surfaces, IndexedDB caching tuned for 3G, five-language TTS. Generic phrases like "passionate developer" are noise.
- **Quote the site's own numbers**: role titles, durations (48 hours → 18 months), stacks. They're already specific; don't inflate them and don't invent metrics the site doesn't state.
- Lead with the **industry match** when one exists; with the **hardest technical requirement** when one doesn't.
- Turn the **design career and teaching work** into role-specific arguments, not biography. Design → customer experience, brand judgment, design-to-code fidelity. Teaching → explaining trade-offs to non-technical stakeholders, and documentation discipline.
- Match **tempo** to what the JD values: Hotbite (48 hours) for speed under deadline; Narvo News (18 months) or OlamideVerse (13 months) for long-haul ownership.
- **Nigeria-first engineering** is a differentiator for Nigerian and Africa-focused employers: Paystack, Naira handling, 3G optimisation, local-language localisation. Say it plainly.
- **AI development & productivity tooling:** For roles valuing engineering velocity, modern AI workflows, AI-assisted development, or prompt engineering, highlight his advanced proficiency with AI development and productivity tools (Gemini Codex, ChatGPT, Claude, and similar AI CLI tools / coding assistants), backed by custom agent skill authoring (Vibe Secure Me) and production AI integrations (Narvo News, Mark_me, Heka IQ).
- Where the JD names a tool he hasn't used, do **not** claim it. Use the substitution table at the end of `profile.md` — name the transferable thing he shipped and let the parallel do the work.

### Link safety — do not skip this

Eight project repos are **private and return 404** to anyone not signed in: `zora`, `hekaiq`,
`negotivity`, `sonasdigital`, `Job-Hustles-Recruiting-Platform`, and the three
`Narvo-Intelligence/*` repos. Sending a recruiter to a 404 is worse than sending nothing.

Cite the **live product URL**, the **App Store listing**, or the portfolio project page instead.
Live URLs in `projects.md` were confirmed reachable on 2026-08-12 (ANC portfolio page added
2026-08-16 — no separate live product URL captured yet). Public repos safe to link are listed in
`profile.md` — `vibe-secure-me` joined that list on 2026-08-12.

Also: the projects index is **`/projects`**, not `/work`. Verify any project link against
`projects.md` before writing it.

## Step 4 — Write the message

Produce **two versions** unless told otherwise.

**A. Primary email** — 250–350 words. Tight beats long; an ATS truncates and a human skims.

- **To** and **Subject** lines. If the posting dictates a subject line, reproduce it **verbatim** — it's often an inbox filter.
- One-sentence opener naming the role and the single most relevant thing about him. Never "I am writing to apply for the position advertised."
- Two or three evidence blocks, plain paragraphs or a short list — what it was, what he built, why it maps to their brief. Use their words for the skill, not a synonym.
- One short paragraph on the non-obvious differentiators — the design-to-engineering arc, the teaching, the ownership. Only if it earns its space; cut it if the email is already tight.
- Availability and logistics: location, on-site vs remote, start date.
- The links, each on its own line.
- Sign-off block: name, title, email, phone, LinkedIn.

**B. Short version** — 100–150 words for WhatsApp, a LinkedIn DM, a recruiter reply, or an
application form's free-text box. Same evidence, stripped to claims and links.

## Voice — write like he'd actually say it

Read the draft back and ask: would a person say this out loud to someone they respect? If not, cut it.

- **Direct, not decorated.** Say the thing, then stop. No throat-clearing, no closing flourish that restates the opener.
- **Confident, not boastful.** State what he built and let the fact carry the weight. Don't editorialize on top of it ("which is a huge achievement", "an incredible opportunity to"). The achievement speaks; adjectives on top of it read as insecure.
- **No sugarcoating.** Skip filler softeners — "I would love the opportunity to", "I truly believe", "I am confident that I". State it plainly: "I built X. It does Y." If a claim is thin, say less about it rather than dressing it up.
- **Short sentences, varied rhythm.** A string of same-length sentences reads as generated. Mix a short line with a longer one that carries a real clause.
- **Specific over generic.** A number, a stack, a timeframe beats an adjective every time. "Shipped in 48 hours" beats "fast-paced environment."
- **One idea per sentence.** No stacked clauses trying to prove three things at once.

Banned outright — none of these survive a first draft, never mind a final one: "I am excited to
apply", "passionate about", "proven track record", "results-driven", "leverage", "synergy",
"I believe I would be a great fit", "dynamic", "cutting-edge", "seamlessly", "utilize", "in today's
fast-paced world", "I am confident that", "look forward to the opportunity to discuss further" —
and any sentence that would survive unchanged in an application to a different company.

Nigerian-professional register: courteous, not deferential. "Kind regards" closes well.

## ATS compliance — the message has to clear a parser before a person reads it

Most applications, especially through a company portal, run through an Applicant Tracking System
before a human sees them. Format for that first, without making the email read like a form.

- **Plain text structure.** No tables, columns, text boxes, images, icons, or headers/footers in the
  body. A markdown draft is fine here — strip the markdown to plain punctuation before it goes into
  a form field or a plain-text email client (bold becomes nothing; a bullet becomes a hyphen).
- **Standard section order.** Subject/opener → fit → evidence → logistics → links → sign-off. Don't
  bury the role title or the strongest match inside a paragraph three lines down.
- **Mirror the JD's own keywords once, verbatim.** If the posting says "REST APIs," write "REST
  APIs," not "RESTful services." ATS keyword matching is literal; a synonym he's technically correct
  to use can still miss the filter.
- **Spell out the role title from the posting at least once**, exactly as written — some parsers
  gate on an exact string match against the job title.
- **Links as plain URLs on their own line**, not hyperlinked text ("click here", "my portfolio") —
  some parsers strip the href and keep only the anchor text, losing the URL entirely.
- **No special characters** beyond standard punctuation — no em-dash-heavy formatting, no bullet
  glyphs (•, ▸), no emoji. Use a plain hyphen for lists.
- **Standard fonts and no design elements** apply to the CV/attachment, not this skill's output —
  but flag it in the "Confirm before sending" list if the posting requires a specific file format
  (e.g. ".docx not PDF") since some parsers still fail on PDF.

## Step 5 — Flag, don't assume

After the drafts, add a short **"Confirm before sending"** list covering every assumption:

- **Location and work mode** — he is in **Lagos**. Flag any assumption about relocation, commute, or on-site work.
- **Salary** — omit it when the posting states a figure. If a form demands an expectation, ask him for a number; never invent one, and never negotiate against himself in a first message.
- **Attachments** — restate what the posting asked for (CV, portfolio, GitHub, cover letter, samples) and whether the draft references an attachment he must actually attach.
- **Sensitive verticals** — Nego is an adult-adjacent companionship marketplace. When citing it, lead with the technical substance (wallet, escrow, Paystack, tiered access control) and flag the vertical so he can decide. For conservative or family-brand employers, prefer Zora as the payments example.
- **Fidia framing** — if the draft cites his co-founder experience at Fidia, confirm it says "Co-Founder & Brand/Visual Designer" (not "Design Lead") and doesn't link getfidia.com (dead since the 2023 closure).
- **Anything you softened** because the evidence was thin, so he can strengthen it if you were wrong.

Optionally close with **one** portfolio observation — a gap this specific posting exposed that's
worth fixing before a recruiter clicks through. Only when genuinely useful; skip rather than invent.

## Hard rules

- **Never fabricate.** No invented metrics, employers, dates, certifications, or tools. If it isn't in `profile.md`, `projects.md`, or a fresh fetch, it doesn't go in the message.
- **Never link a private repo.** See Link safety above.
- **Always include** portfolio, CV, and GitHub in the primary email; at least portfolio and GitHub in the short version.
- **Every draft clears both checks above** — Voice (no banned phrases, no boasting, no filler) and ATS compliance (plain structure, verbatim keywords, plain URLs) — before it's shown to him.
- Output drafts as copy-pasteable markdown in the reply. Only write files when asked.
- Never send anything anywhere. Drafting only — he sends it.
