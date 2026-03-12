# Codex Project Scaffold

This repository is a base scaffold for making an empty repository Codex-ready.

It is the template source, not the project you build in day to day.

Use it when you want to start a new project in:

- an empty directory
- an already initialized empty Git repository
- a new directory that should be initialized as a Git repository during scaffolding

## Start Here

If you are new to this project, this is the shortest path:

```sh
FRAMEWORK=/path/to/codex-project-scaffold
"$FRAMEWORK/bin/codex-scaffold" /path/to/my-project --project-name "My Project" --git-init
cd /path/to/my-project
```

Then open the generated repository in Codex and start with:

```text
Read AGENTS.md, .codex/project.yml, and the docs folder. Then help me set up this project for the first feature.
```

## What This Creates

The scaffold creates:

- `AGENTS.md` for repository-specific operating rules
- `.codex/project.yml` for stable paths and commands
- `docs/` for long-lived project context
- `skills/` for repo-owned Codex skills
- empty `src/` and `tests/` roots

## Use It With Codex

The easiest mental model is:

- this scaffold prepares a repository for Codex
- you then open the generated repository and do the actual project work there

### First-Time Workflow

1. Create a new project folder or empty Git repository.
2. Run this scaffold into that target.
3. Open the generated repository in Codex.
4. Ask Codex to read the repo instructions and docs first.
5. Fill in the project brief and architecture.
6. Set the real `setup`, `run`, and `test` commands in `.codex/project.yml`.
7. Start giving Codex real implementation tasks.

### What To Fill In After Scaffolding

These are the first files you should update:

- `docs/project-brief.md`
- `docs/architecture.md`
- `docs/conventions.md`
- `docs/tasks.md`
- `.codex/project.yml`

### How Codex Should Work In The Generated Repo

Codex should usually work in this order:

1. Read `AGENTS.md`.
2. Read `.codex/project.yml`.
3. Read `docs/project-brief.md`, `docs/architecture.md`, `docs/conventions.md`, and `docs/tasks.md`.
4. Use matching repo-owned skills from `skills/` when relevant.
5. Implement code in `src/` and tests in `tests/`.
6. Update docs when the project changes.

### What You Need To Maintain Over Time

To keep Codex effective, keep these current:

- `docs/project-brief.md`
- `docs/architecture.md`
- `docs/tasks.md`
- `.codex/project.yml`
- any repo-specific skills in `skills/`

## Use Multiple Codex Agents

If you are a first-time user, start with one Codex agent first. That is the simplest way to learn the workflow.

When you are ready to use multiple Codex agents, give each agent a narrow role and keep file ownership clear.

### Safe Multi-Agent Rules

- Do not let multiple agents edit the same files at the same time.
- Give every agent the same starting context: `AGENTS.md`, `.codex/project.yml`, and the docs.
- Use separate branches or separate Git worktrees for parallel work.
- Merge their work through one final integration pass.
- Re-run tests and update docs after merging.

### Good First Multi-Agent Setup

- Planner agent: updates `docs/project-brief.md`, `docs/architecture.md`, and `docs/tasks.md`
- Builder agent: implements the feature in `src/` and `tests/`
- Reviewer agent: checks the result, tests, and documentation alignment

### Skills And Multiple Agents

This scaffold already includes `skills/project-maintainer/`.

If you later want a more specialized multi-agent setup, add more repo-owned skills such as:

- `skills/planner`
- `skills/backend-builder`
- `skills/reviewer`

Then each agent can be instructed to use the skill that matches its role.

### Recommended Progression

1. Start with one Codex agent.
2. Build one real feature.
3. Add a second agent for planning or review.
4. Move to full parallel multi-agent work only after the repo structure and workflow feel stable.

## Command Examples

Assume this scaffold repository is cloned at:

```text
/path/to/codex-project-scaffold
```

All command examples below assume:

```sh
FRAMEWORK=/path/to/codex-project-scaffold
```

Basic syntax:

```sh
"$FRAMEWORK/bin/codex-scaffold" [target-dir] [--project-name <name>] [--force] [--git-init]
```

### New Empty Directory With An Explicit Project Name

```sh
"$FRAMEWORK/bin/codex-scaffold" /path/to/empty-repo --project-name my-service
```

### New Git Repository In One Step

```sh
"$FRAMEWORK/bin/codex-scaffold" /path/to/empty-repo --project-name my-service --git-init
```

### Existing Empty Git Repository

```sh
git init /path/to/empty-repo
"$FRAMEWORK/bin/codex-scaffold" /path/to/empty-repo --project-name my-service
```

### Current Directory

```sh
cd /path/to/empty-repo
"$FRAMEWORK/bin/codex-scaffold" . --project-name my-service
```

### Current Directory With Git Initialization

```sh
mkdir -p /path/to/empty-repo
cd /path/to/empty-repo
"$FRAMEWORK/bin/codex-scaffold" . --project-name my-service --git-init
```

### Use The Folder Name As The Project Name

If you omit `--project-name`, the script derives the project name from the target directory name.

```sh
"$FRAMEWORK/bin/codex-scaffold" /path/to/inventory-service
```

### Use A Display Name That Differs From The Folder Name

```sh
"$FRAMEWORK/bin/codex-scaffold" /path/to/inventory-service --project-name "Inventory Service"
```

In that case:

- the displayed project name is `Inventory Service`
- the generated slug becomes `inventory-service`

### Overwrite Existing Files

```sh
"$FRAMEWORK/bin/codex-scaffold" /path/to/repo --project-name my-service --force
```

### Show Help

From the scaffold source repository root:

```sh
./bin/codex-scaffold --help
```

## What Happens When You Run It

1. The script copies everything from `templates/base/` into the target repository.
2. If you pass `--git-init`, it initializes the target as a Git repository first.
3. It renders placeholders for `__PROJECT_NAME__` and `__PROJECT_SLUG__`.
4. The target repository is left with the base Codex operating structure.

## Generated Repository

### Structure

```text
.
|-- AGENTS.md
|-- .codex/
|   `-- project.yml
|-- docs/
|   |-- project-brief.md
|   |-- architecture.md
|   |-- conventions.md
|   |-- tasks.md
|   `-- decisions/
|-- skills/
|   `-- project-maintainer/
|-- src/
`-- tests/
```

### What Each Part Is For

`AGENTS.md`

- tells Codex how to work in the generated repository
- defines what files to read first
- explains where code and docs belong

`.codex/project.yml`

- acts as the machine-readable repository index
- defines source, test, docs, and skill paths
- holds the `setup`, `run`, and `test` commands

`docs/`

- stores the long-lived project context
- keeps the project brief, architecture, conventions, and tasks in one place

`skills/`

- stores repo-owned Codex skills
- starts with `skills/project-maintainer/`

`src/` and `tests/`

- provide empty starting points for code and tests

## Diagrams

### Source To Target

```mermaid
flowchart LR
    A["This scaffold repository"] --> B["bin/codex-scaffold"]
    C["templates/base"] --> B
    B --> D["Empty target repository"]
    D --> E["AGENTS.md"]
    D --> F[".codex/"]
    D --> G["docs/"]
    D --> H["skills/"]
    D --> I["src/ and tests/"]
```

### Generated Repository Shape

```mermaid
flowchart TD
    A["Generated repository"] --> B["AGENTS.md"]
    A --> C[".codex/project.yml"]
    A --> D["docs/"]
    A --> E["skills/project-maintainer/"]
    A --> F["src/"]
    A --> G["tests/"]
    D --> D1["project-brief.md"]
    D --> D2["architecture.md"]
    D --> D3["conventions.md"]
    D --> D4["tasks.md"]
    D --> D5["decisions/"]
```

### How Codex Uses It

```mermaid
flowchart LR
    A["Open repository"] --> B["Read AGENTS.md"]
    B --> C["Read .codex/project.yml"]
    C --> D["Read docs/ and matching skills/"]
    D --> E["Implement in src/ and tests/"]
    E --> F["Update docs and decisions"]
    F --> G["Run checks from .codex/project.yml"]
```

## Example Session

```sh
mkdir -p /tmp/inventory-service
FRAMEWORK=/path/to/codex-project-scaffold
"$FRAMEWORK/bin/codex-scaffold" /tmp/inventory-service --project-name inventory-service --git-init
cd /tmp/inventory-service
```

At that point the repository is ready for Codex. A normal next prompt would be:

```text
Read AGENTS.md and the docs, then scaffold the first API slice for inventory items.
```

## Extend The Scaffold

### Add More Repo-Owned Skills

1. Add a folder under `templates/base/skills/<skill-name>/`.
2. Create `SKILL.md`.
3. Optionally add `agents/openai.yaml`.
4. Keep the skill concise and repository-specific.

### Extend The Base Template

Put shared files in `templates/base/` when every scaffolded repository should receive them.

## Optional Additions

This scaffold is intentionally minimal. Depending on the project, you may also want:

- CI workflows under `.github/workflows/`
- lint and formatting config
- `.env.example`
- container setup
- deployment docs
- runbooks
- additional repo-specific skills

## Verification

The scaffold has been verified to:

- print `--help`
- scaffold a base-only repository into a temporary directory
- initialize and scaffold a Git repository with `--git-init`
- preserve the repo-owned skill and docs structure in the generated repository
