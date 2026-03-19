# AGENTS.md

This repository is operated with Codex as the primary coding agent.

## Shared Team Contract

Treat this file as the shared operating contract for all Codex sessions in the repository.

- Every Codex session should read this file first.
- If the team learns a repeat lesson or recurring mistake, add the smallest durable rule that would have prevented it.
- Keep rules short and operational here, and move longer rationale to `docs/decisions/` when needed.

## Start Here

Before changing code, read:

1. `.codex/project.yml`
2. `docs/project-brief.md`
3. `docs/plan.md`
4. `docs/architecture.md`
5. `docs/conventions.md`
6. `docs/tasks.md`

## Expectations

- Keep implementation aligned with `docs/project-brief.md`.
- Update `docs/plan.md` when milestones, sequencing, or dependencies change.
- Update `docs/architecture.md` when design or boundaries change.
- Update `docs/conventions.md` when workflow or code conventions change.
- Update `docs/tasks.md` when starting or finishing substantial work.
- Prefer small, testable changes over broad speculative rewrites.
- Run the relevant checks before finishing if commands are defined.
- Use repo-owned skills from `skills/` when the task matches them.

## Shared Mistakes And Lessons

Use this file to capture team-wide rules that came from real mistakes.

- Add short "do this, not that" rules when something repeats.
- Prefer durable rules over one-off history.
- Remove or rewrite rules that are no longer useful.

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
