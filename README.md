# AI Role System

A generic 7-role AI collaboration workflow for solo developers. Works with 50+ coding agents via the open [skills.sh](https://skills.sh/) ecosystem.

## What is this?

This skill collection defines a structured pipeline where AI assumes one of seven roles at a time — each with clear responsibilities, boundaries, and handoff protocols. The roles form a chain:

```
/pm → /ui → /arch → /dev → /qa → /review → /ops
```

Each role reads project configuration from a single binding file (`role-project.md`), so the skills themselves stay project-agnostic and portable across repositories.

## Roles

| Prefix | Role | Responsibility |
|--------|------|----------------|
| `/pm` | Product Manager | Clarify requirements, write PRD handoffs |
| `/ui` | UI Designer | Page structure, states, field display |
| `/arch` | Architect | Technical design, module boundaries, API contracts |
| `/dev` | Developer | Implement from arch handoff, write dev-log |
| `/qa` | QA | Run tests, write qa-report, trigger rollback |
| `/review` | Code Reviewer | Blocking/non-blocking review, boundary compliance |
| `/ops` | Ops/Release | Ship checklist, CI guidance, commit messages |

Plus `role-init` to bootstrap the system onto a new repository, and `ai-role-collaboration` as the orchestration skill that ties everything together.

## Install

### Install all skills (recommended)

```bash
npx skills add qiaogr199/ai-role-system -g -y
```

### Install individual roles

```bash
npx skills add qiaogr199/ai-role-system@role-init -g -y
npx skills add qiaogr199/ai-role-system@role-pm -g -y
npx skills add qiaogr199/ai-role-system@ai-role-collaboration -g -y
# ... etc.
```

### Quick start in a new project

1. Install the skills
2. Run `role-init` — it generates project-specific config (`role-project.md`, `AGENTS.md`, handoff templates)
3. Start with `/pm your-feature-idea`

## How it works

### Destructive vs fast path

Not every change needs the full pipeline. The system distinguishes:

- **Destructive** (full handoff required): API contract changes, schema migrations, cross-module dependencies, auth/workflow changes
- **Fast path**: Bug fixes, single-module refactors, comments/logs

When unsure, default to destructive (the principle is: when in doubt, be strict).

### Handoffs

Each role writes a structured handoff document before passing to the next:

| Role | Output |
|------|--------|
| `/pm` | `01-pm-brief.md` |
| `/ui` | `02-ui-spec.md` (skip if no UI) |
| `/arch` | `03-arch-design.md` |
| `/dev` | `04-dev-log.md` + code |
| `/qa` | `05-qa-report.md` |
| `/review` | `06-review.md` |
| `/ops` | `07-ship.md` |

### Rollback protocol

QA failures roll back to `/dev`. Review can block on implementation (back to `/dev`) or design (back to `/arch`). Three or more rollbacks trigger re-architecture.

## Port to another repo

1. Copy `.agents/skills/role-*` and `ai-role-collaboration` to the target repo
2. Copy the cursor rule (`role-router.md`) or generate via `role-init`
3. Run `role-init` in the target repo

The skills are generic. All project-specific facts live in `role-project.md`.

## Directory structure

```
ai-role-system/
  skills/
    ai-role-collaboration/   # Orchestration skill
      SKILL.md
      metadata.json
      reference.md
    role-init/               # Bootstrap for new repos
      SKILL.md
      metadata.json
      templates/             # Handoff & config templates
    role-pm/                 # Product Manager
    role-ui/                 # UI Designer
    role-arch/               # Architect
    role-dev/                # Developer
    role-qa/                 # QA
    role-review/             # Code Reviewer
    role-ops/                # Ops/Release
  skills.sh.json             # skills.sh directory manifest
```

## License

MIT
