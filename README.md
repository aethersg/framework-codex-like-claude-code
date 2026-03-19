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
Read AGENTS.md, .codex/project.yml, docs/plan.md, and the rest of the docs. Then help me set up this project for the first feature.
```

## What This Creates

The scaffold creates:

- `AGENTS.md` for repository-specific operating rules
- `.codex/project.yml` for stable paths and commands
- `docs/` for long-lived project context
- `docs/plan.md` for milestones, sequencing, and dependencies
- `skills/` for repo-owned Codex skills
- empty `src/` and `tests/` roots

## Use It With Codex

The easiest mental model is:

- this scaffold prepares a repository for Codex
- you then open the generated repository and do the actual project work there

### Shared Rule: Use `AGENTS.md` As The Shared Codex Contract

Whether one person uses Codex or a whole team uses it, treat `AGENTS.md` as the single shared instruction set for every Codex session in the repository.

That means:

- every team member should tell Codex to read `AGENTS.md` first
- recurring mistakes should be turned into short rules in `AGENTS.md`
- team-wide preferred patterns should live in `AGENTS.md`
- longer explanations can live in `docs/decisions/`, but the operational rule should still be summarized in `AGENTS.md`

The goal is that one person's mistake becomes a rule that helps the whole team next time.

### Plan Vs Tasks

The scaffold now separates execution strategy from live status:

- `docs/plan.md`: milestones, phases, sequencing, workstreams, and dependencies
- `docs/tasks.md`: current backlog, in-progress work, and completed work

That separation matters once a team is involved or one developer is running multiple Codex sessions. The plan explains how work should be sequenced. The task list shows what is actually moving right now.

### Shared Starter Prompt

This is a good default prompt for everyone:

```text
Read AGENTS.md first and follow it. If you find a recurring mistake or a team rule that should be shared, propose an update to AGENTS.md before finishing.
```

### Shared Knowledge Flow

```mermaid
flowchart LR
    A["Developer opens Codex"] --> B["Codex reads AGENTS.md first"]
    B --> C["Codex reads .codex/project.yml and docs/"]
    C --> D["Codex implements work"]
    D --> E{"Did we learn a durable lesson?"}
    E -- "No" --> F["Finish task"]
    E -- "Yes" --> G["Add short rule to AGENTS.md"]
    G --> H["Add longer rationale to docs/decisions if needed"]
    H --> I["Future sessions inherit the lesson"]
```

## One Person Using Codex

This is the simplest mode and the best place to start.

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
- `docs/plan.md`
- `docs/architecture.md`
- `docs/conventions.md`
- `docs/tasks.md`
- `.codex/project.yml`

### Prompt Order For One Person

Use these prompts in order after generating the scaffold.

1. Read-in prompt

```text
Read AGENTS.md first, then .codex/project.yml, docs/project-brief.md, docs/plan.md, docs/architecture.md, docs/conventions.md, and docs/tasks.md. Summarize what is missing before we start building.
```

2. Project brief prompt

```text
Help me fill docs/project-brief.md. Ask only the minimum questions needed, then draft the file with a clear problem, users, success criteria, and non-goals.
```

3. Plan prompt

```text
Draft docs/plan.md from the brief. Propose phases, milestones, dependencies, risks, and the next review point. Keep it practical and small.
```

4. Architecture prompt

```text
Draft docs/architecture.md to match the brief and plan. Keep the initial design minimal, name the main components, interfaces, and constraints, and call out what can wait.
```

5. Commands and conventions prompt

```text
Based on the chosen stack, update docs/conventions.md and fill setup, run, and test in .codex/project.yml. If the stack is still undecided, propose the smallest sensible default.
```

6. Task breakdown prompt

```text
Turn the plan into an initial docs/tasks.md with a small backlog, one in-progress slice, and clear done criteria for the first milestone.
```

7. First implementation prompt

```text
Implement the smallest useful first slice. Update src/, tests/, docs/tasks.md, and any other docs that changed. Stop and explain tradeoffs before making broad architectural choices.
```

8. Review and lessons prompt

```text
Review the changes, run the relevant checks, update docs/plan.md or docs/tasks.md if needed, and propose any durable AGENTS.md rule we learned.
```

### One-Person Prompt Flow

```mermaid
flowchart LR
    A["Read repo context"] --> B["Draft project brief"]
    B --> C["Draft plan"]
    C --> D["Draft architecture"]
    D --> E["Set commands and conventions"]
    E --> F["Create tasks"]
    F --> G["Implement first slice"]
    G --> H["Review and capture lessons"]
```

### How Codex Should Work In The Generated Repo

Codex should usually work in this order:

1. Read `AGENTS.md`.
2. Read `.codex/project.yml`.
3. Read `docs/project-brief.md`, `docs/plan.md`, `docs/architecture.md`, `docs/conventions.md`, and `docs/tasks.md`.
4. Use matching repo-owned skills from `skills/` when relevant.
5. Implement code in `src/` and tests in `tests/`.
6. Update docs when the project changes.

### What You Need To Maintain Over Time

To keep Codex effective, keep these current:

- `docs/project-brief.md`
- `docs/plan.md`
- `docs/architecture.md`
- `docs/tasks.md`
- `.codex/project.yml`
- any repo-specific skills in `skills/`
- `AGENTS.md` whenever the team learns a durable new rule

## A Team Using Codex

If multiple developers use Codex in the same repository, the team needs one shared operating model.

### What The Team Should Standardize

- everyone tells Codex to read `AGENTS.md` first
- everyone uses the same `docs/` and `.codex/project.yml` as the source of truth
- recurring mistakes get turned into short rules in `AGENTS.md`
- longer explanations go into `docs/decisions/`
- repo-wide shared skills are committed into `skills/`

### Good Team Process

1. Keep `AGENTS.md` short and operational.
2. Add rules only when they are durable and team-wide.
3. Update `docs/plan.md` when the execution approach changes, and update `docs/tasks.md` so others can see what is active now.
4. Review `AGENTS.md` changes the same way you review code changes.
5. Remove stale rules when they stop being useful.

### Prompt Order For Teams

These prompts work well for a shared team setup.

1. Shared read-in prompt

```text
Read AGENTS.md first, then .codex/project.yml, docs/project-brief.md, docs/plan.md, docs/architecture.md, docs/conventions.md, and docs/tasks.md. Propose any missing team-wide rules we should agree on before work starts.
```

2. Shared brief prompt

```text
Draft docs/project-brief.md for team review. Keep it concise and make scope, users, success criteria, and non-goals easy to challenge before implementation starts.
```

3. Shared plan prompt

```text
Draft docs/plan.md for team review. Split the work into phases, milestones, workstreams, dependencies, and risks. Make the workstreams small enough for separate developers or Codex sessions to own.
```

4. Shared architecture prompt

```text
Draft docs/architecture.md for the first milestone. Mark what is decided now, what stays intentionally open, and what should not be built yet.
```

5. Shared work split prompt

```text
Turn the current plan into docs/tasks.md with the first backlog, the next in-progress slice, and file ownership guidance for parallel work. Keep overlapping file edits to a minimum.
```

6. Shared skills prompt

```text
Propose any repo-owned skills under skills/ that the whole team should share for recurring workflows. Only suggest skills that are clearly reusable across multiple developers.
```

7. Developer or agent execution prompt

```text
Read AGENTS.md, .codex/project.yml, docs/plan.md, and the relevant docs first. Own only these files: <paths>. Implement only task <task-name>, update docs/tasks.md with progress, and propose an AGENTS.md update if you find a repeat lesson.
```

8. Integration prompt

```text
Review the current diff against the brief, plan, and architecture. Reconcile docs/tasks.md, update docs/plan.md if sequencing changed, and list any team-wide AGENTS.md rules we should add before merge.
```

### Team Prompt Flow

```mermaid
flowchart LR
    A["Shared read-in"] --> B["Agree brief"]
    B --> C["Agree plan"]
    C --> D["Agree architecture"]
    D --> E["Split work and assign ownership"]
    E --> F["Developers or Codex sessions implement owned work"]
    F --> G["Integrate, review, and update AGENTS.md"]
```

### What To Put In `AGENTS.md`

Good content for `AGENTS.md`:

- what files Codex must read first
- repository layout rules
- coding and testing expectations
- team-wide "do this, not that" lessons
- when to use repo-owned skills

Avoid putting these in `AGENTS.md`:

- long historical notes
- detailed architecture explanations
- task-specific one-off instructions

Those belong in `docs/decisions/`, `docs/architecture.md`, `docs/plan.md`, or `docs/tasks.md`.

### Team Flow

```mermaid
flowchart LR
    A["Team member starts Codex session"] --> B["Read AGENTS.md"]
    B --> C["Read .codex/project.yml, plan, and docs/"]
    C --> D["Do task"]
    D --> E{"Found repeat mistake or better rule?"}
    E -- "No" --> F["Open PR with code/docs changes"]
    E -- "Yes" --> G["Update AGENTS.md"]
    G --> H["Optionally update docs/decisions"]
    H --> F
    F --> I["Team reviews and merges"]
    I --> J["Next team member uses updated AGENTS.md"]
```

## Sharing Skills With The Whole Team

If a skill should be shared by everyone, commit it into the repository under `skills/`.

That is the difference between:

- personal workflow: lives in one person's local setup
- team workflow: lives in the repository under `skills/`

### When A Skill Should Be Shared

Share a skill when:

- the whole team wants Codex to follow the same workflow
- the same task is repeated across developers
- the same mistakes keep happening
- the skill is part of how the repository is supposed to work

### Good Shared Skill Examples

- `skills/planner`
- `skills/backend-builder`
- `skills/reviewer`
- `skills/migration-writer`

### Rule Of Thumb

If only one person needs it, keep it personal.

If the repository depends on it, commit it under `skills/`.

### Personal Vs Shared Skills

```mermaid
flowchart TD
    A["New skill or workflow idea"] --> B{"Only useful to one person?"}
    B -- "Yes" --> C["Keep it in personal local setup"]
    B -- "No" --> D{"Needed for how the repo should work?"}
    D -- "No" --> E["Keep evaluating before sharing"]
    D -- "Yes" --> F["Commit skill under skills/"]
    F --> G["Reference it from AGENTS.md when needed"]
    G --> H["Whole team uses the same workflow"]
```

## One Developer Running Multiple Codex Sessions

This is different from a whole team. Here one developer is running multiple Codex sessions in parallel for speed.

Use this when one person wants to split work into separate lanes.

### Safe Rules For Multiple Sessions

- give each session a narrow job
- do not let two sessions edit the same files at the same time
- use separate branches or separate Git worktrees if the sessions run in parallel
- give every session the same starting context: `AGENTS.md`, `.codex/project.yml`, `docs/plan.md`, and the rest of the docs
- merge the results through one final review pass

### Good Single-Developer Multi-Session Split

- Session 1: update `docs/project-brief.md`, `docs/plan.md`, `docs/architecture.md`, and `docs/tasks.md`
- Session 2: build the feature in `src/` and `tests/`
- Session 3: review the result and check docs consistency

### When Not To Use Multiple Sessions

Avoid it when:

- the repository is still unclear
- the task is small
- multiple sessions would touch the same files
- the overhead is larger than the work itself

### Single-Developer Multi-Session Flow

```mermaid
flowchart LR
    A["One developer starts multiple Codex sessions"] --> B["Each session reads AGENTS.md, plan, and docs/"]
    B --> C["Session 1: planning/docs"]
    B --> D["Session 2: implementation"]
    B --> E["Session 3: review"]
    C --> F["Merge results"]
    D --> F
    E --> F
    F --> G["Run tests and update docs"]
```

## Team Multi-Agent Use

This is the heaviest mode: multiple people and multiple Codex agents or sessions.

Keep roles narrow and file ownership clear.

### Safe Multi-Agent Rules

If you are a first-time user, start with one Codex agent first. That is the simplest way to learn the workflow.

When you are ready to use multiple Codex agents, give each agent a narrow role and keep file ownership clear.

- Do not let multiple agents edit the same files at the same time.
- Give every agent the same starting context: `AGENTS.md`, `.codex/project.yml`, `docs/plan.md`, and the rest of the docs.
- Treat `AGENTS.md` as the shared operating contract for all agents.
- Use separate branches or separate Git worktrees for parallel work.
- Merge their work through one final integration pass.
- Re-run tests and update docs after merging.

### Good First Multi-Agent Setup

- Planner agent: updates `docs/project-brief.md`, `docs/plan.md`, `docs/architecture.md`, and `docs/tasks.md`
- Builder agent: implements the feature in `src/` and `tests/`
- Reviewer agent: checks the result, tests, and documentation alignment

### Skills And Multiple Agents

This scaffold already includes `skills/project-maintainer/`.

If you later want a more specialized multi-agent setup, add more repo-owned skills such as:

- `skills/planner`
- `skills/backend-builder`
- `skills/reviewer`

Then each agent can be instructed to use the skill that matches its role.

## Recommended Strategies

Use the lightest strategy that solves the problem.

### Strategy Selection Flow

```mermaid
flowchart TD
    A["Need Codex help"] --> B{"Small or unclear task?"}
    B -- "Yes" --> C["One person, one session"]
    B -- "No" --> D{"One developer can split work cleanly?"}
    D -- "Yes" --> E["One person, multiple sessions"]
    D -- "No" --> F{"Team needs shared behavior?"}
    F -- "Yes" --> G["Team with shared AGENTS.md"]
    F -- "No" --> C
    G --> H{"Stable workflows and shared skills?"}
    H -- "No" --> G
    H -- "Yes" --> I["Team with shared skills and multi-agent workflow"]
```

### Strategy 1: One Person, One Session

Best for:

- new repositories
- first-time users
- small features
- unclear tasks

### Strategy 2: One Person, Multiple Sessions

Best for:

- medium-sized work that splits cleanly
- one developer doing planning, build, and review in parallel
- situations where file ownership can stay separate

### Strategy 3: Team, Shared `AGENTS.md`, Mostly Single Sessions

Best for:

- teams that want consistent Codex behavior
- shared lessons and repeatable workflows
- gradual Codex adoption without too much process overhead

### Strategy 4: Team, Shared Skills, Multi-Agent Workflow

Best for:

- mature teams with stable repo rules
- repeated work patterns
- larger parallel efforts with clear boundaries

### Recommended Progression

1. Start with one Codex agent.
2. Build one real feature.
3. Start using `AGENTS.md` as the shared rules file.
4. Share repo-wide skills under `skills/`.
5. Add a second session or agent for planning or review.
6. Move to full parallel multi-agent work only after the repo structure and workflow feel stable.

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
|   |-- plan.md
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
- acts as the shared team contract for all Codex sessions
- captures durable lessons from recurring mistakes

`.codex/project.yml`

- acts as the machine-readable repository index
- defines source, test, docs, and skill paths
- holds the `setup`, `run`, and `test` commands

`docs/`

- stores the long-lived project context
- keeps the project brief, plan, architecture, conventions, and tasks in one place

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
    D --> D2["plan.md"]
    D --> D3["architecture.md"]
    D --> D4["conventions.md"]
    D --> D5["tasks.md"]
    D --> D6["decisions/"]
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
Read AGENTS.md, docs/plan.md, and the rest of the docs, then scaffold the first API slice for inventory items.
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
