---
id: 2f1c7af8-ac25-457e-a74f-2611a8dad3cf
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# The Tinderbox

A Tinderbox is a directory that holds many Flints and shared code repositories as one declared unit. The declaration is a file, `tinderbox.toml`, kept in git. The command `flint tinderbox sync` materialises that declaration on the current machine.

NUU Cognition keeps its own product Flints in one Tinderbox. Each product has its own Flint inside the box.

## What the declaration holds

- **Members.** The Flints in the box. A member is `own`, so the box clones it from a git URL into a folder under the box root. Or a member is `reference`, so the box points at a copy that already exists on the machine. A member is `required` or `optional`.
- **Repos.** Code repositories shared across the box. Each repo is exposed to all member Flints or to a named subset. An exposed repo appears in each Flint as a codebase reference.
- **Connections.** Which Flints reference each other. A connection is a directed edge or an interconnected group.

## Commands

All `flint tinderbox` commands walk up from the current directory to find `tinderbox.toml`. They run from the box root or from inside any member.

```bash
flint tinderbox init <name>          # make an empty Tinderbox here
flint tinderbox init --from <url>    # clone an existing Tinderbox, then sync
flint tinderbox sync                 # materialise members, repos, connections
flint tinderbox status               # per member: mode, present, wired
flint tinderbox check                # read-only drift check
```

Take care with `sync`, `import`, and `heal`. They can move or delete Flints on disk. Use `--dry-run` first.

## The Tinderbox as an entity

A Tinderbox is an entity of its own. It has an id, kept in `tinderbox.json`, and it holds its members as references. Membership is a relation from the Tinderbox to the Flint. The Tinderbox is never part of the address of a Flint. See [[Addresses]].

On the network, the Tinderbox folder is a place. It can answer `describe` and `children`, so another machine can list the members of the box, when visibility allows. See [[The NUU Network]] and [[Organisations and Visibility]].

## Where to go next

- [[What a Flint Is]] for the members of a box.
- [[Typed Flints]] for the kinds of Flint that a box can hold.
