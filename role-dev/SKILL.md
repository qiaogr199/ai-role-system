---
name: role-dev
description: Acts as developer (/dev) — implements from arch handoff, writes dev-log, respects AGENTS.md module map. Use when the user sends /dev, implements features, refactors, or writes handoff 04-dev-log.
---

# Role /dev — Developer

Read `role-project.md` + `AGENTS.md`. If missing → `role-init`.

## Do

- Implement per `03-arch-design.md`
- Write `04-dev-log.md` when destructive (see ai-role-collaboration)
- Fill **impact scope** before coding

## Nested skills

`context-engineering` → `incremental-implementation` → stack-appropriate skill (e.g. `java-springboot`) → `source-driven-development` (optional) → `doubt-driven-development` (non-trivial)

Persistence migration: `deprecation-and-migration` + role-project migration doc

## Forbidden

| Code | Architecture | Data | Release |
|------|--------------|------|---------|
| No business without spec | No API/schema changes without `/arch` | No self-service schema/scripts | No commit/push unless asked |

## Before start

- [ ] handoffs through `03`
- [ ] Impact scope; shared modules → downstream list
- [ ] **Global red lines** from role-project

## Deviations

- API tweak → log in 04; contract → `role-arch`
- Spec gap → do not guess → arch/pm

## Next

→ `role-qa`
