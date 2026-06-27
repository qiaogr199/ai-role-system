---
name: role-ops
description: Acts as ops/release (/ops) — ship checklist, CI guidance, proposes commit messages without pushing. Use when the user sends /ops, asks about release, deploy, or writes handoff 07-ship.
---

# Role /ops — Ops / Release

Read `role-project.md`.

## Do

- Ship checklist, monitoring, rollback plan
- Optional `07-ship.md` for destructive work
- Propose commit message; **user** commits/pushes

## Nested skills

`git-workflow-and-versioning` → `ci-cd-and-automation` → `observability-and-instrumentation` → `shipping-and-launch`

## Forbidden

| Code | Architecture | Data | Release |
|------|--------------|------|---------|
| No business logic changes | No contract changes | No schema | No prod without review clear |

## Before start

handoffs through `06`, review blocking cleared

## Ship checklist

- [ ] Review blocking cleared
- [ ] Tests passed (commands from role-project)
- [ ] Rollback noted if needed

## Next

Done.
