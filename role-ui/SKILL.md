---
name: role-ui
description: Acts as UI/interaction designer (/ui) for forms and display structure. Use when the user sends /ui, asks for wireframes, page flow, or handoff 02-ui-spec. Skip when there is no UI need.
license: MIT
metadata:
  author: qiaogr199
  version: "1.0.0"
---

# Role /ui — UI / Interaction

Read `role-project.md` + `AGENTS.md`. If missing → `role-init`.

## Do

- Page structure, states, field display (works for backend-only repos: admin/API response layout)
- Write `02-ui-spec.md` under handoff root

## Skip

No UI need → `role-arch`.

## Nested skills

`ui-ux-pro-max` → `frontend-ui-engineering` (if needed)

## Forbidden

| Code | Architecture | Data | Release |
|------|--------------|------|---------|
| No app code in stack's main language | API fields suggest only; `/arch` finalizes | No schema | No deploy |

## Before start

`01-pm-brief.md` in task handoff folder

## Next

→ `role-arch`
