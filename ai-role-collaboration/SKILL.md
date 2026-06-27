---
name: ai-role-collaboration
description: Orchestrates the generic 7-role AI workflow (/pm /ui /arch /dev /qa /review /ops), handoff directories, and role switching. Use when the user sends a role prefix, mentions handoff, AI roles, role-init, or asks which role to use.
---

# AI Role Collaboration

Generic seven-role workflow for solo AI-assisted development. **Project-specific paths and red lines** live in `.agents/project/role-project.md` (create via `role-init`).

## Bootstrap

If `.agents/project/role-project.md` is **missing** → run `role-init` before using roles.

## Role map

| Prefix | Skill | Handoff output |
|--------|-------|----------------|
| `/pm` | `role-pm` | `01-pm-brief.md` |
| `/ui` | `role-ui` | `02-ui-spec.md` (skip if no UI) |
| `/arch` | `role-arch` | `03-arch-design.md` |
| `/dev` | `role-dev` | `04-dev-log.md` + code |
| `/qa` | `role-qa` | `05-qa-report.md` |
| `/review` | `role-review` | `06-review.md` |
| `/ops` | `role-ops` | `07-ship.md` |

Skills: `.agents/skills/role-*/SKILL.md` · Router: `.cursor/rules/role-router.md`

## Project binding (always read)

From `role-project.md`:

- `agents_map`, `handoff_root`, `handoff_templates`
- `build` / `test` / `test_scoped` commands
- **Global red lines**, shared modules, migration doc, core entry points

From `AGENTS.md` (path in role-project): module map.

## When a prefix arrives

1. Read `role-project.md` + `AGENTS.md`
2. Read matching `role-*` skill
3. Read required handoffs ([reference.md](reference.md))
4. Stay within role boundaries

No prefix → keep previous role; first message defaults to `/dev`.

## Pipeline

```
/pm → /ui? → /arch → /dev → /qa → /review → /ops
```

Rollback: `/dev ←back qa` · review blocking → dev/arch · ≥3 rollbacks → re-architect.

## Handoffs

Root path from `role-project.md` (convention: `doc/ai-handoffs/{date}-{slug}/`).

Meta: `<!-- handoff-meta: role=... | ... -->` · Templates: `{handoff_templates}/`

## Destructive vs fast path

**Destructive** (handoff required, at least `03` + `04`): API contract, schema, persistence layer migration, cross-module deps, auth/workflow, deletes, core entry behavior change (see role-project **Core entry points**).

**Fast path**: contract-preserving bug fix, single-module refactor, comments/logs.

When unsure → destructive (**宁严勿松**).

## Nested workflow skills

Each role invokes **one** skill at a time from `.agents/skills/` (e.g. `incremental-implementation`). Do not load full chains at once.

## Port to another repo

1. Copy `.agents/skills/role-*`, `ai-role-collaboration`, `role-init`
2. Copy `.cursor/rules/role-router.md` (or use template from role-init)
3. Run `role-init` in target repo

Details: [reference.md](reference.md)
