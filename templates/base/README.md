# __PROJECT_NAME__

This repository was scaffolded for Codex-driven development.

## Working Files

- `AGENTS.md`: repository-specific instructions for Codex and the shared team contract for Codex sessions.
- `.codex/project.yml`: stable project metadata and command references.
- `docs/project-brief.md`: product intent and scope.
- `docs/plan.md`: delivery phases, milestones, dependencies, and sequencing.
- `docs/architecture.md`: technical design and boundaries.
- `docs/conventions.md`: implementation and workflow conventions.
- `docs/tasks.md`: active backlog and progress tracking.
- `skills/`: repo-owned skills Codex can use for recurring workflows.

## Team Workflow

- Tell Codex to read `AGENTS.md` first in every session.
- Treat `AGENTS.md` as the shared rules file for the whole team.
- When a mistake repeats or a better rule is discovered, update `AGENTS.md` so future sessions inherit it.
- Keep the rule short in `AGENTS.md` and put longer rationale in `docs/decisions/` when needed.
- Keep `docs/plan.md` focused on execution strategy and keep `docs/tasks.md` focused on live task status.

## First Prompt Order

### One Person

Use these prompts in order:

1. `Read AGENTS.md first, then .codex/project.yml, docs/project-brief.md, docs/plan.md, docs/architecture.md, docs/conventions.md, and docs/tasks.md. Summarize what is missing before we start building.`
2. `Help me fill docs/project-brief.md. Ask only the minimum questions needed, then draft the file.`
3. `Draft docs/plan.md from the brief with phases, milestones, dependencies, risks, and the next review point.`
4. `Draft docs/architecture.md to match the brief and plan. Keep the initial design minimal.`
5. `Update docs/conventions.md and fill setup, run, and test in .codex/project.yml based on the chosen stack.`
6. `Turn the plan into docs/tasks.md with a small backlog and one in-progress slice.`
7. `Implement the smallest useful first slice and keep docs/tasks.md current.`
8. `Review the changes, update docs/plan.md or docs/tasks.md if needed, and propose any durable AGENTS.md rule we learned.`

### Team

Use these prompts in order:

1. `Read AGENTS.md first, then .codex/project.yml and docs/. Propose any missing team-wide rules we should agree on before work starts.`
2. `Draft docs/project-brief.md for team review. Keep the scope easy to challenge before implementation starts.`
3. `Draft docs/plan.md for team review with phases, milestones, workstreams, dependencies, and risks.`
4. `Draft docs/architecture.md for the first milestone and mark what stays intentionally open.`
5. `Turn the current plan into docs/tasks.md with work ownership guidance for parallel work.`
6. `Propose any repo-owned skills under skills/ that the whole team should share for recurring workflows.`
7. `Read AGENTS.md, .codex/project.yml, docs/plan.md, and the relevant docs first. Own only these files: <paths>. Implement only task <task-name> and update docs/tasks.md with progress.`
8. `Review the diff against the brief, plan, and architecture. Reconcile docs/tasks.md, update docs/plan.md if sequencing changed, and propose any AGENTS.md rules to add before merge.`

## Commands

Set `setup`, `run`, and `test` in `.codex/project.yml` once the project runtime is chosen.
