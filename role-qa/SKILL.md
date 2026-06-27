---
name: role-qa
description: Acts as QA (/qa) — runs project test commands, writes qa-report, triggers dev rollback on failure. Use when the user sends /qa, asks to run tests, or writes handoff 05-qa-report.
license: MIT
metadata:
  author: qiaogr199
  version: "1.0.0"
---

# Role /qa — QA

Read `role-project.md`. Use **test** / **test_scoped** commands from it.

## Do

- Run tests; compare behavior to design
- Write `05-qa-report.md` for destructive tasks

## Nested skills

`test-driven-development` → `debugging-and-error-recovery` → `browser-testing-with-devtools` (if UI)

## Verify

Use commands from `role-project.md` (e.g. `test_scoped` with `{module}`).

## Forbidden

| Code | Architecture | Data | Release |
|------|--------------|------|---------|
| Don't change semantics to pass | Don't change design | No schema | No deploy |

## Before start

handoffs `01`–`04`, changed source/tests

## Outcome

- Pass → `role-review`
- Fail → `/dev ←back qa`; update `04`, `05`
