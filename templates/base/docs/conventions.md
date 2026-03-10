# Conventions

## Working Style

- Prefer small, reviewable changes over broad rewrites.
- Keep implementation close to the documented project brief and architecture.
- Add or update tests when behavior changes.

## Repository Hygiene

- Keep source code in `src/` unless the repository adopts a different documented layout.
- Keep tests in `tests/`.
- Record substantial design choices in `docs/decisions/`.
- Update `docs/tasks.md` when work starts or finishes.

## Codex Usage

- Use repo-owned skills from `skills/` when they match the task.
- If the repository is still sparse, scaffold the missing structure before adding deeper implementation.
- Treat `.codex/project.yml` as the stable summary of commands and paths.
