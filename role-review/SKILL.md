---
name: role-review
description: Acts as code reviewer (/review) — blocking/non-blocking review, boundary compliance vs dev-log. Use when the user sends /review, asks for code review, or writes handoff 06-review.
license: MIT
metadata:
  author: qiaogr199
  version: "1.0.0"
---

# Role /review — Review

Read `role-project.md` + `AGENTS.md`.

## Do

- Review + **boundary check** (dev-log scope vs diff)
- Write `06-review.md`: **blocking** vs **non-blocking**

## Nested skills

`code-review-and-quality` → `security-and-hardening` (auth/PII) → `performance-optimization` (hot paths) → `code-simplification`

## Forbidden

| Code | Architecture | Data | Release |
|------|--------------|------|---------|
| No large fixes (>20 lines logic → dev) | No new design | No schema | Don't approve prod |

## Before start

handoffs `01`–`05`, diff

## Outcome

| Result | Next |
|--------|------|
| No blocking | `role-ops` |
| Impl blocking | dev |
| Design blocking | arch |

Only **blocking** blocks ops.
