---
id: 2286c5ce-3aba-4873-b19b-8eb88851db9a
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# What a Flint Is

A Flint is a workspace: a directory that the Flint CLI manages. It organises human knowledge and agent capabilities together. A person and a terminal agent, such as Claude Code or Codex, work in it side by side.

On the surface, a Flint looks like a modded Obsidian vault. Underneath, it is a Mesh editor. Everything is plain markdown in folders. There is no database and no lock-in. It works with Obsidian, git, and any text editor.

## The three layers

| Folder | Layer | Holds |
|---|---|---|
| `Mesh/` | Content | All notes and typed artifacts. See [[The Mesh]]. |
| `Media/` | Content | Images, PDFs, and other non-markdown files. |
| `Shards/` | Capabilities | The cognitive programs that an agent can load. See [[Shards]]. |

A Flint can also reference code repositories and other Flints through its `flint.toml`. Agents then know where the code is and can navigate to it.

## Why the structure matters

The key insight of Flint is simple. Give an AI agent a well-structured workspace with clear conventions, typed artifacts, and explicit instructions, and it can do a wide range of knowledge work: project management, writing, research, documentation, and coding.

Every Flint has one system file, `Mesh/(System) Flint Init.md`. It says what the Flint is about, how to navigate it, and which shards are installed. An agent reads it first in every session.

## The workspace as a program

A Flint is a runtime for cognitive programs. In the words of the public pitch:

- The Mesh is the memory. Artifacts persist between sessions.
- The shards are the instructions: skills, workflows, and templates.
- The agent runtime is the processor.
- The CLI is the interface to the outside world.

Everything is written in plain English instead of code. The execution is a language model that follows instructions on markdown files.

## Identity

A Flint has a person identity: the operator's Name. It is set once per machine with `flint setup`, and it is the same for every Flint on that machine. When an agent creates a note, it writes the person as the author, as a wikilink to `Mesh/People/@<Name>.md`. The person is the author. The agent acts on behalf of the person.

## Kinds of Flint

Most Flints are plain Flints. A plain Flint has a type, a preset, and an optional org. A preset is a shard list for a new Flint. Three more types exist for special jobs: the Computer Flint, the Guide, and the Member Flint. See [[Typed Flints]].

Many Flints can live together in one box. See [[The Tinderbox]].

## Where to go next

- [[The Mesh]] for what goes inside.
- [[Shards]] for what an agent can do.
- [[How to Install and Start]] to make your first Flint.
