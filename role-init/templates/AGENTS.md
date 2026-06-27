# {PROJECT_NAME}

> AI context map. Project binding: `.agents/project/role-project.md`

## Tech Stack

{STACK_BULLETS}

## Commands

- Build: `{BUILD_CMD}`
- Test: `{TEST_CMD}`

## Module Map

| Module / Package | Responsibility | Key entry |
|------------------|----------------|-----------|
| {name} | {what it does} | {controller, main, or —} |

Add rows from codebase scan.

## Shared module rules

High-risk shared areas (from role-project.md): changes default to **destructive** handoff.

## Boundaries

Load full list from `.agents/project/role-project.md` → **Global red lines**.

## AI role system

- Orchestration: `.agents/skills/ai-role-collaboration/SKILL.md`
- Init / re-bind: `.agents/skills/role-init/SKILL.md`
- Handoffs: `{handoff_root}/` (see role-project.md)

## /dev startup checklist

- [ ] Read `.agents/project/role-project.md` and relevant handoffs
- [ ] Confirmed impact modules / packages
- [ ] Confirmed destructive vs fast-path handoff
