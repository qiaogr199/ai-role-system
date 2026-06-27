# AI Role Collaboration — Reference

All paths/commands/red lines: **`.agents/project/role-project.md`**

## New session — required reads

| Role | Handoff files | Also read |
|------|---------------|-----------|
| `/pm` | — | role-project.md, AGENTS.md |
| `/ui` | 01 | role-project.md, AGENTS.md |
| `/arch` | 01, 02? | + migration doc from role-project if applicable |
| `/dev` | through 03 | + source to edit |
| `/qa` | 01–04 | + tests |
| `/review` | 01–05 | + diff |
| `/ops` | 01–06 | |

## Rollback

| Trigger | Target | Update |
|---------|--------|--------|
| QA fail | `/dev` | 04, 05 |
| Review impl blocking | `/dev` | 06 |
| Review design blocking | `/arch` | 03 |
| Spec gap | `/arch` or `/pm` | no guessing |
| Ship fail | `/dev` or `/qa` | 07 |

Same `{date}-{slug}` folder; append rollback in `04-dev-log.md`.

## Gray zone

| Case | Owner | Action |
|------|-------|--------|
| API field tweak | `/dev` | log in 04; contract change → `/arch` |
| Incomplete spec | `/arch` `/pm` | backfill handoff |
| Destructive dispute | `/arch` | 宁严勿松 |
| Shared/high-risk module | `/arch` first | list downstream (from role-project) |
| Bug fix changes behavior | `/arch` | destructive handoff |

## Destructive checklist (customize in role-project)

Use **Core entry points** and **Shared modules** tables in `role-project.md`.

## Universal defaults (override in role-project)

- No secrets in git
- Schema/data changes need `/arch` + documented scripts path
- User owns commit/push unless asked

## Init another project

Invoke `role-init` → generates `role-project.md`, `AGENTS.md`, handoff scaffold.
