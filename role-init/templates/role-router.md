---
description: AI role router — parses /pm /arch /dev prefixes; loads generic role skills + project binding
alwaysApply: true
---

# Role Router

Generic 7-role workflow. **Project facts:** Read `.agents/project/role-project.md` first.

If `role-project.md` is missing → follow `.agents/skills/role-init/SKILL.md` to initialize.

## Parse rules

1. Prefixes: `/pm` `/ui` `/arch` `/dev` `/qa` `/review` `/ops`; rollback: `/dev ←back qa`
2. On match → Read `.agents/skills/role-{name}/SKILL.md`
3. No prefix → keep previous role; first message defaults to `/dev`
4. One message → first prefix only
5. Switch only after handoff ready or explicit path declared

## Role → Skill

| Prefix | Skill |
|--------|-------|
| `/pm` | `.agents/skills/role-pm/SKILL.md` |
| `/ui` | `.agents/skills/role-ui/SKILL.md` |
| `/arch` | `.agents/skills/role-arch/SKILL.md` |
| `/dev` | `.agents/skills/role-dev/SKILL.md` |
| `/qa` | `.agents/skills/role-qa/SKILL.md` |
| `/review` | `.agents/skills/role-review/SKILL.md` |
| `/ops` | `.agents/skills/role-ops/SKILL.md` |

Orchestration: `.agents/skills/ai-role-collaboration/SKILL.md`

## Handoffs

Paths from `role-project.md` (default `doc/ai-handoffs/{date}-{slug}/`).

- Meta: `<!-- handoff-meta: ... -->` (not body)
- Destructive: at least `03-arch-design.md` + `04-dev-log.md`
- Downstream rejects incomplete upstream handoffs

## Red lines

Read **Global red lines** from `.agents/project/role-project.md` — not hardcoded in this file.

## Rollback

QA fail → `/dev ←back qa` · Review blocking → dev/arch · ≥3 rollbacks → re-architect

## Context

- Prefer handoff files over long chat history
- ≤3 consecutive roles per session; then new session + handoff path

## New session

User provides: `/role` + handoff directory. Read `role-project.md`, `AGENTS.md`, required handoffs, then act.
