---
id: abf167b2-6a69-426a-802a-99a04610205a
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
  - "[[b61b6398-0bf0-4b33-81ef-df08f56f2fc5]]"
---

# How to Ask This Guide

This Flint is a Guide about NUU Cognition. A person clones it, opens it with an agent, and asks questions. The agent reads the notes and answers from them.

## How to ask

1. Open an agent session in the root of this Flint.
2. Ask one question at a time.
3. Give the name of the thing that you ask about. "What is a shard?" is better than "What is that thing?".
4. Say who you are, when it matters: a new person, a developer, or an agent. The answer can then match your level.
5. When the agent names the notes that it used, open them. The note is the source. The answer is a summary.

## What the agent does

- It reads `Mesh/(System) Flint Init.md` first, then the note that fits.
- It answers from the notes of this Guide first, and it names them.
- When the notes have no answer, it says so. It does not guess. It points you to the public docs.
- When two notes disagree, it prefers the newer one, and it tells you.
- For a Flint question or a Flint problem, it loads the Flint Help shard (`flint shard start fh`). Flint Help also reads the installed CLI and the Flint source code in `Sources/Repos/Flint Public/`.

## Ask about a Flint problem

1. Run the command again, and copy the full output. Do not cut it.
2. Give the command, the folder where you ran it, and what you expected.
3. The agent explains the cause, names the evidence, and gives the next command. It asks you before it runs a command that changes your files.

## Good questions for this Guide

- What is NUU Cognition, in one paragraph?
- What is the difference between a Flint, a Mesh, and a shard?
- What does a Guide Flint do, and how is it different from a Member Flint?
- How do I install Flint and make my first workspace?
- `flint sync` says `blocked`. What do I do?
- What does `private`, `org`, and `public` mean for a Flint?
- What is an address, and how do I read `@my-org/flint/my-notes`?

## Questions outside this Guide

This Guide is a front door. It is not the knowledge base. It does not hold:

- Internal plans, tasks, or meeting notes of NUU Cognition.
- Source code details of products other than Flint. For Flint, Flint Help reads the copy of the Flint source in `Sources/Repos/Flint Public/`.
- Facts about a person, beyond a public author line.
- Anything private to one org or one machine.

For those, the agent will say that the question is outside the Guide.

## How to keep the Guide correct

- Write one subject per note. Use short sentences.
- Put the date on a fact that can change.
- The visibility is `public`. Write nothing here that only one org may read.
- Add a new note instead of making an old note long. Link it from the Init file.

## Where to go next

- [[Glossary]] for one line per term.
- [[What NUU Cognition Is]] to start reading.
