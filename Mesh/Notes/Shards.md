---
id: a3d619e0-6399-4bff-8ed0-acb2e475f27a
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# Shards

A shard is a cognitive program. It is a self-contained package that extends what an agent can do inside a Flint. Without shards, a Flint is an empty workspace. With shards, it becomes a structured environment for planning, building, and tracking work.

Shards are an evolution of agent skills. The key difference is state. A shard runs inside a Flint, so it can persist artifacts in the Mesh. Workflows can build on top of each other and compound.

Shards are written in plain English. No code is required.

## What a shard contains

| File | Purpose |
|---|---|
| `shard.yaml` | The manifest: name, version, dependencies, and what it installs. |
| `init-<sh>.md` | The context. An agent reads it first. It defines the rules of the shard. |
| `skills/sk-<sh>-<name>.md` | Skills: single-purpose tasks with no human checkpoint. |
| `workflows/wkfl-<sh>-<name>.md` | Workflows: multi-stage tasks with human review between stages. |
| `templates/tmp-<sh>-<name>-v<X.X>.md` | Templates: instructions for how to create an artifact. |
| `knowledge/knw-<sh>-<name>.md` | Knowledge: deep reference material. |
| `install/` | Files copied into the workspace: dashboards, type definitions. |

`<sh>` is the short name of the shard, for example `proj` for Projects.

## Examples

- **Flint** (`f`): the core environment. It defines the rules of the workspace and the shape of notes.
- **Projects** (`proj`): task management. Tasks are the unit of work, with a lifecycle from `todo` to `done`.
- **Notepad** (`ntpd`): persistent, editable conversations with numbered sections, forks, and derived artifacts.
- **Invironments** (`ie`): the section and group tags that structure a flat Mesh.
- **Orbh** (`foh`): headless session management. See [[Agents and Orbh Sessions]].

The public registry lists more. It includes shards for agentic coding, specifications, reports, plans, guides, and meetings.

## How an agent loads a shard

1. Run `flint shard start <name>`. The output lists the init file, the required reading, and the skills, workflows, templates, and knowledge.
2. Read the init file and the required reading in full.
3. Only then use a skill, a workflow, or a template.

An agent loads shards on demand. It never loads all shards at once.

## How a person installs a shard

```bash
flint shard list                 # what is installed
flint shard install owner/repo   # install from a repository
flint shard update               # update installed shards
```

A shard can be installed, or in development. A shard in development lives in a `(Dev Remote)` or `(Dev Local)` folder and can be edited. An installed shard is overwritten on update.

## Where to go next

- [[The Mesh]] for what shards write.
- [[Agents and Orbh Sessions]] for who runs them.
- `shards.nuucognition.com` for the registry.
