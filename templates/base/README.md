# __PROJECT_NAME__

This repository was scaffolded for Codex-driven development.

## Working Files

- `AGENTS.md`: repository-specific instructions for Codex and the shared team contract for Codex sessions.
- `.codex/project.yml`: stable project metadata and command references.
- `docs/project-brief.md`: product intent and scope.
- `docs/architecture.md`: technical design and boundaries.
- `docs/conventions.md`: implementation and workflow conventions.
- `docs/tasks.md`: active backlog and progress tracking.
- `skills/`: repo-owned skills Codex can use for recurring workflows.

## Team Workflow

- Tell Codex to read `AGENTS.md` first in every session.
- Treat `AGENTS.md` as the shared rules file for the whole team.
- When a mistake repeats or a better rule is discovered, update `AGENTS.md` so future sessions inherit it.
- Keep the rule short in `AGENTS.md` and put longer rationale in `docs/decisions/` when needed.

## Commands

Set `setup`, `run`, and `test` in `.codex/project.yml` once the project runtime is chosen.
