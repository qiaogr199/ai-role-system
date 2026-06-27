# AGENTS.md

This file provides guidance to AI coding agents (Claude Code, Cursor, Copilot, etc.) when working with code in this repository.

## Repository Overview

A collection of generic AI collaboration skills for solo developers. Provides a structured 7-role pipeline (/pm /ui /arch /dev /qa /review /ops) with clear boundaries, handoff protocols, and rollback support.

## Directory Structure

```
skills/
  {skill-name}/           # kebab-case directory name
    SKILL.md              # Required: skill definition with YAML frontmatter
    metadata.json         # Required: skill metadata (version, abstract)
    templates/            # Optional: supporting templates (role-init only)
    reference.md          # Optional: reference documentation
    PACKAGING.md          # Optional: packaging/porting documentation
```

## Naming Conventions

- **Skill directory**: `kebab-case` (e.g., `role-init`, `ai-role-collaboration`)
- **SKILL.md**: Always uppercase, always this exact filename
- **Templates**: Markdown templates in `templates/` subdirectory

## SKILL.md Format

```markdown
---
name: {skill-name}
description: {One sentence describing when to use this skill. Include trigger phrases like "/pm", "/dev", etc.}
license: MIT
metadata:
  author: qiaogr199
  version: "1.0.0"
---

# {Skill Title}

{Skill content}
```

## Skills

| Skill | Role | Pipeline position |
|-------|------|-------------------|
| `ai-role-collaboration` | Orchestration | — |
| `role-init` | Bootstrapper | — |
| `role-pm` | Product Manager | 1st |
| `role-ui` | UI Designer | 2nd (optional) |
| `role-arch` | Architect | 3rd |
| `role-dev` | Developer | 4th |
| `role-qa` | QA | 5th |
| `role-review` | Code Reviewer | 6th |
| `role-ops` | Ops/Release | 7th |

## Installation

```bash
npx skills add qiaogr199/ai-role-system -g -y
```
