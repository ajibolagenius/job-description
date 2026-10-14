# `/jd` Skill

Turn a job description into a tailored application message for Ajibola Akelebe.

Accepts a JD as pasted text, a URL, a screenshot, or earlier conversation context. Produces a primary
email and a shorter recruiter/application-form version. Every claim must come from the candidate
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

Read `profile.md` for every application; read `projects.md` when the role needs project evidence.

## Workflow

1. Provide a complete job description (ask if it's missing).
2. Read `profile.md` and the relevant parts of `projects.md`.
3. Extract required qualifications, preferred skills, responsibilities, and company context.
4. Choose the two or three strongest evidence points as the spine; expand to four to six labeled
   blocks for senior or lead roles when each answers a different requirement.
5. Write the primary email and the short version, in the letter register defined in `SKILL.md`.
6. Close with a `Confirm before sending` list: location and work mode, salary, attachments, every
   unclaimable required skill, employer-internal numbers, sensitive verticals, framing cautions.

## Guardrails

- Never invent experience, dates, tools, metrics, employers, or qualifications.
- Never link a private repository; use a live product URL, the App Store listing, or the portfolio project page.
- Always include portfolio, CV, and GitHub in the primary email; add the App Store link for mobile, e-commerce, and consumer-product roles.
- Describe Branda V2 as a 24-hour screening build, never as client work for Branda, and never imply real payments.
- Describe Fidia as `Co-Founder & Brand/Visual Designer`; never link getfidia.com.
- Describe Zora as an app built and shipped by Ajibola, not one he published (it ships under ZORA AFRICA LIMITED, 0 reviews).
- State 3+ years professional software engineering, 5+ years design, 10+ years combined.
- Claim tiers decide phrasing: production-shipped tools claim plainly; tools used once say "has used" / "has deployed on" (this now includes **GCP**); `NestJS` and `Prisma` are "familiar with" only; **Azure and .NET are gaps** and must be named in the gap paragraph.
- Cite Bema Integrated Services (`Full-Stack Software Engineer (Frontend-Strong)`) for Vitest, Playwright, Coolify, Trello and Plane — as employment, never as portfolio work, and without employer-internal test counts in the letter.
- The letter is formal: expanded contractions, no em-dashes, spelled-out acronyms. A letter he has actually sent outranks any draft he edited.
- Never send anything. Drafting only.

## Refresh evidence

Check these first when the snapshot looks stale or the candidate reports a change; update only the
affected files and record the verification date.

- https://ajibolagenius.vercel.app/cv
- https://ajibolagenius.vercel.app/projects
- https://ajibolagenius.vercel.app/sitemap.xml
- https://api.github.com/users/ajibolagenius/repos?per_page=100&sort=pushed

Evidence verified **2026-10-08**; voice, length and gap rules calibrated **2026-10-14**.
