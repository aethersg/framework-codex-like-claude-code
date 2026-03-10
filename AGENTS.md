# AGENTS.md

This repository maintains a reusable scaffold for Codex-driven projects.

## Scope

- Keep shared behavior in `templates/base/`.
- Keep repo-owned skills in `templates/base/skills/`.
- Treat `bin/codex-scaffold` as the entrypoint for applying templates into target repositories.

## Change Rules

- Preserve placeholder names unless the script is updated to render new ones.
- Keep starter skills concise and repo-focused.
- Update the root `README.md` when the scaffold structure or usage changes.

## Verification

- Run `./bin/codex-scaffold --help` after modifying the bootstrap script.
- Test the scaffold against a temporary empty directory before concluding substantial changes.
