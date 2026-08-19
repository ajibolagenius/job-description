# `/jd` Skill

Turn a job description into a tailored application message for Ajibola Akelebe.

The skill supports job descriptions supplied as pasted text, URLs, screenshots, or earlier
conversation context. It produces a primary email and a shorter recruiter or application-form
version. Every claim must come from the candidate evidence files or a fresh source check.

## Canonical Location

This directory is the source of truth:

```text
~/.agents/skills/jd/
```

Keep other agent skill directories linked to this directory. Do not maintain copied versions.

```text
~/.claude/skills/jd  -> ../../.agents/skills/jd
~/.cursor/skills/jd  -> ../../.agents/skills/jd
~/.codex/skills/jd   -> ../../.agents/skills/jd
```

## Files

- `SKILL.md` contains the workflow, writing rules, link policy, and hard constraints.
- `profile.md` contains identity, contact details, education, experience, skills, and evidence mapping.
- `projects.md` contains project details, technology stacks, live links, and project-specific cautions.

Read `profile.md` for every application. Read `projects.md` when the role needs project evidence.

## Usage

1. Provide a complete job description.
2. Read `profile.md` and the relevant sections of `projects.md`.
3. Extract required qualifications, preferred skills, responsibilities, and company context.
4. Select two or three strong, relevant evidence points.
5. Write the primary email and short version.
6. Add a brief `Confirm before sending` section for assumptions about location, salary, attachments,
   and work mode.

If no job description is present, ask for it. Do not write a generic application.

## Guardrails

- Never invent experience, dates, tools, metrics, employers, or qualifications.
- Never link a private repository. Use a live product URL or portfolio project page instead.
- Always include the portfolio, CV, and GitHub links in the primary email.
- Include the App Store link for mobile, e-commerce, and consumer-product roles.
- Describe Fidia as `Co-Founder & Brand/Visual Designer`.
- Describe Zora as an app built and shipped by Ajibola, not as an app he published.
- Treat `NestJS` and `Prisma` as familiar tools, not shipped production experience.

## Refresh Evidence

Refresh the snapshots when they become stale or when the candidate reports a change. Check these
sources first:

- https://ajibolagenius.vercel.app/cv
- https://ajibolagenius.vercel.app/projects
- https://ajibolagenius.vercel.app/sitemap.xml
- https://api.github.com/users/ajibolagenius/repos?per_page=100&sort=pushed

Record the verification date and update only the affected evidence files.

## Output Style

Write directly and use specific evidence. Avoid generic application phrases, inflated claims, and
decorative language. Keep the output suitable for copy and paste into an email or application form.