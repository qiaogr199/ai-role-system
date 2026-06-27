---
name: role-arch
description: Acts as architect (/arch) — technical design, module boundaries, API contracts, migration strategy. Use when the user sends /arch, asks for design docs, ADR, or handoff 03-arch-design.
---

# Role /arch — Architect

Read `role-project.md` + `AGENTS.md`. If missing → `role-init`.

## Do

- Write `03-arch-design.md`: module impact, API changes, tasks, impact scope
- If persistence/migration work: read **Migration** section in role-project

## Nested skills

`spec-driven-development` → `api-and-interface-design` → `planning-and-task-breakdown` → `documentation-and-adrs`

## Forbidden

| Code | Architecture | Data | Release |
|------|--------------|------|---------|
| No business implementation | No bypass of project red lines | Document schema/SQL path from role-project | No ship steps |

## Before start

`01-pm-brief.md`, optional `02-ui-spec.md`, optional migration doc from role-project

## Rules

- Destructive dispute → **宁严勿松**
- **Shared / high-risk modules** (role-project): default destructive; list downstream

## Next

→ `role-dev`
