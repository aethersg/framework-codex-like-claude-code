# AGENTS.md

This repository is operated with Codex as the primary coding agent.

## Start Here

Before changing code, read:

1. `.codex/project.yml`
2. `docs/project-brief.md`
3. `docs/architecture.md`
4. `docs/conventions.md`
5. `docs/tasks.md`

## Expectations

- Keep implementation aligned with `docs/project-brief.md`.
- Update `docs/architecture.md` when design or boundaries change.
- Update `docs/conventions.md` when workflow or code conventions change.
- Update `docs/tasks.md` when starting or finishing substantial work.
- Prefer small, testable changes over broad speculative rewrites.
- Run the relevant checks before finishing if commands are defined.
- Use repo-owned skills from `skills/` when the task matches them.

## Default Layout

- Application code lives under `src/`.
- Tests live under `tests/`.
- Stable project context lives under `.codex/` and `docs/`.
- Reusable repo-specific workflows live under `skills/`.
- Design decisions belong in `docs/decisions/`.

## When The Repo Is Still Sparse

- Scaffold missing files instead of leaving implied structure.
- Document assumptions explicitly in `docs/project-brief.md` or `docs/architecture.md`.
- Keep the first implementation minimal enough to validate the shape of the project.
