---
id: 3f4949d5-6cdb-4cf7-a169-5f1a9f8233d7
tags:
  - "#f/init"
  - "#guide/nuu-cognition"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
  - "[[b61b6398-0bf0-4b33-81ef-df08f56f2fc5]]"
---

# (Guide) NUU Cognition

This Flint is a Guide. A Guide is a public Flint that a person clones and then asks questions of, with an agent. This Guide is about NUU Cognition: what it is, what its parts are, how to start, and where to go next. It is a front door. It is not the knowledge base of NUU Cognition. The reader is a new person or a new agent with no context.

The visibility of this Flint is `public`. It holds nothing private.

## How an agent must use this Guide

1. Read this file first. Then read the note that fits the question.
2. Answer from the notes in `Mesh/Notes/` first. Name the notes that you used.
3. When a question is outside these notes, say so. Do not guess. Point the person to the public docs in the list below.
4. When two notes or two docs disagree, prefer the newer one, and say that they disagree.
5. Write nothing here that only one org or one person may read. Do not add secrets, tokens, machine names, or private facts about a person.
6. When you add or change a note, keep one subject per note, and write in short sentences.

## Flint questions and Flint problems

For a question about Flint, or a problem with a Flint command, load the Flint Help shard: run `flint shard start fh` and read the files that it lists. Flint Help answers from the installed CLI, the notes of this Guide, and the Flint source code in `Sources/Repos/Flint Public/`. It names each source. It asks the person before it runs a command that writes.

## Navigation

Read the notes in this order for a full picture. Each note is short. Each note links to the notes near it.

- [[What NUU Cognition Is]]: the organisation, its goal, and its products in one page.
- [[Thinking Technologies]]: the idea behind the organisation.
- [[Models and Information Environments]]: the theory that shapes every tool.
- [[What a Flint Is]]: the workspace for a person and an agent.
- [[The Mesh]]: the content layer of a Flint.
- [[Shards]]: the capabilities that an agent loads inside a Flint.
- [[Agents and Orbh Sessions]]: how an agent works in a Flint, and how sessions are managed.
- [[The Tinderbox]]: many Flints as one box.
- [[Typed Flints]]: the plain Flint, the Computer Flint, the Guide, and the Member Flint.
- [[Organisations and Visibility]]: what an org is, and who can see what.
- [[Addresses]]: how every thing has a name and an id.
- [[The NUU Network]]: how machines talk to each other, at a high level.
- [[The Other Products]]: Mesh, NCM, Vessel, Surf, Parse, Docs, OrbCode, University.
- [[How to Install and Start]]: the first steps on a new machine.
- [[How to Ask This Guide]]: how to get a good answer from this Guide.
- [[Glossary]]: one line per term.

## Public docs

- `nuucognition.com`: the main website.
- `flint.nuucognition.com`: Flint.
- `shards.nuucognition.com`: the shard registry.
- `mesh.nuucognition.com`: Mesh.
- `ncm.nuucognition.com`: NUU Cognition Markdown.
- `vessel.nuucognition.com`: Vessel.

## Folders

- `Mesh/`: all content of this Guide. `Mesh/Notes/` holds the notes.
- `Media/`: images and other non-markdown files.
- `Shards/`: the capabilities that are installed in this Flint. `Shards/(Source Local) Flint Help/` is the source of the Flint Help shard.
- `Sources/Repos/Flint Public/`: a read-only copy of the Flint source code (`https://github.com/NUU-Cognition/flint-public`). `flint sync` clones it. Do not edit it.
