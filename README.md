# `/jd` Skill

Turn a job description into a tailored application message for Ajibola Akelebe.

Accepts a JD as pasted text, a URL, a screenshot, or earlier conversation context. Produces a primary
email, a shorter recruiter/application-form version, and an ATS keyword match checked against his
ATS CV. Every claim must come from the candidate
evidence files or a fresh source check — never invented.

## Canonical location

This directory is the source of truth; keep other agent skill directories linked, never copied.

```text
~/.agents/skills/jd/
~/.claude/skills/jd  -> ../../.agents/skills/jd
~/.cursor/skills/jd  -> ../../.agents/skills/jd
~/.codex/skills/jd   -> ../../.agents/skills/jd
```

## Files

- `SKILL.md` — workflow, voice and register rules, ATS rules, link policy, hard constraints.
- `profile.md` — identity, contact, education, experience, skills, mapping cheatsheet, claim tiers, never-claim list.
- `projects.md` — project dossiers, stacks, live links, project-specific cautions.
- `~/Desktop/Ajibola/CV — Ajibola - ATS.html` (outside this directory) — the ATS CV he attaches as a PDF. The letter must agree with it; conventions are recorded in `profile.md` → "The ATS CV".

Read `profile.md` and the ATS CV for every application; read `projects.md` when the role needs project evidence.

## Workflow

1. Provide a complete job description (ask if it's missing).
2. Read `profile.md`, the ATS CV, and the relevant parts of `projects.md`.
3. Extract required qualifications, preferred skills, responsibilities, and company context.
4. Choose the two or three strongest evidence points as the spine; expand to four to six labeled
   blocks for senior or lead roles when each answers a different requirement.
5. Write the primary email and the short version, in the letter register defined in `SKILL.md`.
6. Add the ATS keyword match: required and preferred JD keywords counted against the CV (counts,
   never invented scores), with spelling mismatches, CV omissions and unclaimable gaps listed.
7. Close with a `Confirm before sending` list: location and work mode, salary, attachments, every
   unclaimable required skill, employer-internal numbers, sensitive verticals, framing cautions.

## Guardrails

- Never invent experience, dates, tools, metrics, employers, or qualifications.
- Never link a private repository; use a live product URL, the App Store listing, or the portfolio project page. Seven repos are private as of 2026-10-14 (`zora`, `hekaiq`, `negotivity`, `sonasdigital`, `Job-Hustles-Recruiting-Platform`, and `Narvo-Intelligence/narvo_intelligence` and `documentations`).
- **Four `Narvo-Intelligence` repos are public as of 2026-10-14** — `narvo_news`, `narvo_platform`, `legacy_code_2` (the shipping FastAPI backend) and `narvo-app-proto`. Their stacks in `projects.md` were re-read from repo source. In prose call the backend **"the Narvo API"**, never "legacy code", and do not claim the consumer monorepo serves live data (its README records the backend as not yet scaffolded there).
- **Claim scope on the Narvo backend:** "designed and shipped this FastAPI service as a Docker image on Google Cloud Run" is true and now verifiable. "GCP at scale", "GCP architect", Kafka, RabbitMQ, Azure Service Bus, Django, Flask and Airflow are not.
- Always include portfolio, CV, and GitHub in the primary email; add the App Store link for mobile, e-commerce, and consumer-product roles; add the Narvo API repo link for backend, Python, API or AI-infrastructure roles when the application invites code.
- Describe Branda V2 as a 24-hour screening build, never as client work for Branda, and never imply real payments.
- Describe Fidia as `Co-Founder and Brand/Visual Designer`; never link getfidia.com.
- Describe Zora as an app built and shipped by Ajibola, not one he published (it ships under ZORA AFRICA LIMITED, 0 reviews).
- State 3+ years professional software engineering, 5+ years design, 10+ years combined.
- Claim tiers decide phrasing: production-shipped tools claim plainly (includes React, Next.js, TypeScript, FastAPI, Python, PostgreSQL, MongoDB, Expo/React Native, Docker, etc.); tools known and used include **MongoDB** for document schema modelling, collections, indexing and aggregation; tools used once say "has used" / "has deployed on" (this still includes **GCP** as a platform-depth claim, even though the Narvo API's Cloud Run `Dockerfile` is public); **Upstash moved up to production-shipped on 2026-10-14** (its wiring is in the public backend); `NestJS` and `Prisma` are "familiar with" only; **Azure and .NET are gaps** and must be named in the gap paragraph.
- Cite Bema Integrated Services (`Full-Stack Software Engineer (Frontend-Strong)`) for Vitest, Playwright, Coolify, Trello and Plane — as employment, never as portfolio work, and without employer-internal test counts in the letter. **Never frame Bema (or any role) as current employment in generated messages**; frame all experience as past jobs or neutral track-record experience.
- The letter is formal: expanded contractions, no em-dashes, spelled-out acronyms. A letter he has actually sent outranks any draft he edited.
- **One rulebook for the CV and the letter:** the same titles, start years only, the same tool names (the JD's spelling wins when it differs), tool-only skill lists, and no number the CV leaves out.
- **Never specify current employment in generated messages:** always frame roles as past jobs or neutral experience; never write "currently working", "in my current role", or "my current employer".
- Never send anything. Drafting only.

## Refresh evidence

Check these first when the snapshot looks stale or the candidate reports a change; update only the
affected files and record the verification date.

- https://ajibolagenius.vercel.app/cv
- https://ajibolagenius.vercel.app/projects
- https://ajibolagenius.vercel.app/sitemap.xml
- https://api.github.com/users/ajibolagenius/repos?per_page=100&sort=pushed
- https://api.github.com/orgs/Narvo-Intelligence/repos?per_page=100&sort=pushed — check `visibility` here before linking any org repo

Evidence verified **2026-10-08**; voice, length and gap rules calibrated **2026-10-14**; Narvo family
re-verified from repo source **2026-10-14** (four org repos became public that day); ATS CV and skill
aligned **2026-10-15**.
