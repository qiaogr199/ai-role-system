---
name: role-init
description: Initializes the generic 7-role AI collaboration system for the current repository — creates role-project.md, AGENTS.md, handoff templates, and role-router. Use when setting up a new project, when role-project.md is missing, or when the user says role-init, init AI roles, or bootstrap handoff workflow.
license: MIT
metadata:
  author: qiaogr199
  version: "1.0.0"
---

# Role Init

Bootstraps the **generic** role skill system onto **this repository**. Skills in `.agents/skills/role-*` stay project-agnostic; all project facts live in generated files below.

## Before you start

1. Confirm repo root (where `.git` or root build file lives)
2. Scan stack: `pom.xml`, `package.json`, `go.mod`, `Cargo.toml`, etc.
3. If `.agents/project/role-project.md` exists → ask user: **re-init** (merge) or **skip**

## Outputs (create or update)

| File | Purpose |
|------|---------|
| `.agents/project/role-project.md` | **Binding manifest** — paths, commands, red lines |
| `AGENTS.md` | Module map, boundaries (from template + scan) |
| `doc/ai-handoffs/_templates/*` | Handoff templates (if missing) |
| `doc/ai-handoffs/_index.md` | Task index (if missing) |
| `.cursor/rules/role-router.md` | Router rule (if missing or user asks refresh) |
| `.agents/roles/README.md` | Quick reference (if missing) |

Templates: [templates/](templates/)

## Workflow

### Step 1 — Discover

Gather from codebase + user (ask only what scan cannot answer):

- Project name and one-line purpose
- Build / test commands
- Module or package boundaries (top-level dirs)
- Optional: migration docs, shared modules, critical entry classes
- Optional: custom red lines

### Step 2 — Write `role-project.md`

Use [templates/role-project.md](templates/role-project.md). Fill every section; leave optional blocks as `none` if N/A.

**Rule:** After init, skills read **only** this file for project paths and red lines — never hardcode project names inside skills.

### Step 3 — Write `AGENTS.md`

Use [templates/AGENTS.md](templates/AGENTS.md). Include:

- Tech stack, commands (copy from role-project)
- Module map table (from scan)
- Pointer: `.agents/project/role-project.md`
- Pointer: `.agents/skills/ai-role-collaboration/SKILL.md`

### Step 4 — Scaffold handoffs

If missing, copy templates from `.agents/skills/role-init/templates/handoffs/` to `doc/ai-handoffs/_templates/`.

Initialize `_index.md` with header only if missing.

### Step 5 — Router + README

If `.cursor/rules/role-router.md` missing, copy [templates/role-router.md](templates/role-router.md).

Ensure it references `.agents/project/role-project.md` for red lines and paths.

### Step 6 — Verify

```markdown
Init checklist:
- [ ] role-project.md exists and paths resolve
- [ ] AGENTS.md Module Map matches repo layout
- [ ] handoff _templates present (01, 03, 04 minimum)
- [ ] role-router.md points to generic skills + role-project.md
- [ ] User told: use `/pm` … `/ops` or invoke `ai-role-collaboration`
```

Optional Step 0 smoke test: `/pm` → `/arch` → `/dev` on a dummy handoff folder (no code changes).

## Re-init / porting existing project

When migrating from an already-configured repo:

1. Extract facts from existing `AGENTS.md`, docs, CI config into `role-project.md`
2. Do **not** delete existing handoff history under `doc/ai-handoffs/`
3. Update `role-project.md` `Init history` table

## What role-init does NOT do

- Does not copy `.agents/skills/role-*` (skills are shared/generic)
- Does not modify application business code
- Does not commit unless user asks

## After init

Tell the user:

```
AI role system ready.
- Config: .agents/project/role-project.md
- Start: /pm your feature idea  OR  invoke skill ai-role-collaboration
- Re-bind another repo: copy .agents/skills/role-* + run role-init there
```

## Additional resources

- Generic orchestration: [../ai-role-collaboration/SKILL.md](../ai-role-collaboration/SKILL.md)
- Example filled config (reference only): see any repo's `.agents/project/role-project.md`
