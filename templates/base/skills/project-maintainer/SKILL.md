---
name: project-maintainer
description: Use this skill when working inside this repository to scaffold missing structure, keep project docs in sync with code changes, and follow the repo's local operating conventions.
---

# Project Maintainer

## Overview

This skill keeps work aligned with the repository's local operating model. Use it when implementing features, bootstrapping sparse areas of the repo, or updating docs that Codex is expected to maintain alongside code.

## Workflow

1. Read `.codex/project.yml` for the current paths and commands.
2. Read `docs/project-brief.md`, `docs/plan.md`, `docs/architecture.md`, `docs/conventions.md`, and `docs/tasks.md`.
3. If the repo is still sparse, scaffold the smallest missing structure needed before writing deeper implementation.
4. Keep code, tests, and docs consistent with each other.
5. When architecture, workflow, or scope changed, update the corresponding docs before finishing.

## Expectations

- Prefer minimal changes that keep the repo coherent.
- Do not leave task tracking stale after substantial work.
- Keep `docs/plan.md` about sequencing and milestones, and keep `docs/tasks.md` about live task state.
- Put reusable project-specific logic in the repo rather than only in chat context.
- Add a decision record in `docs/decisions/` when a design choice is likely to matter later.

## When To Avoid This Skill

- Do not use this skill for purely global machine setup.
- Do not use this skill when another repo-owned skill is more specific to the task.
