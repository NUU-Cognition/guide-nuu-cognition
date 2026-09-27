---
id: dd19442b-db22-40ff-8a2c-7457b4600c32
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# Typed Flints

Every Flint has a type. Four types exist. The type is closed and fixed in code. It sets the folder prefix, how many Flints of that type may exist, the required relations, and the default visibility.

| Type | Folder prefix | How many | Relations | Default visibility |
|---|---|---|---|---|
| `flint` | `(Flint)` | Any number | None | `org` when it has an org, else `private` |
| `computer` | `(Computer)` | One per machine | `of`: the machine | `private` |
| `guide` | `(Guide)` | Any number | `about`: optional | `public` |
| `member` | `(Member)` | One per person per org | `owner`: the person, `regarding`: the org | `private`, locked |

## Type and preset are two axes

A **type** is what the Flint is for. A **preset** is the shard list of a new Flint. Presets are open data. The shipped presets are `quarry`, `lab`, `library`, `factory`, `observatory`, `garden`, and `forum`. A preset never appears in an address. A type does: `@my-org/flint.guide/my-guide`. See [[Addresses]].

## The plain Flint

The plain Flint is the general workspace. See [[What a Flint Is]]. Its shards write its Mesh. It has no starter note.

## The Computer Flint

The Computer Flint is the model of one machine. One machine has one Computer Flint. It holds the model of the hardware, the operating system, the accounts, and the network names. It records which Tinderboxes and Flints are on the machine, and the results of health checks. Its visibility is `private`, so other machines cannot read it through the network. It holds no secrets. Secrets stay in the home directory of the user, not in a Flint, because a Flint can travel in git.

## The Guide

A Guide is a Flint that a person clones and asks questions of, with an agent. It is public by default. It can be `about` one entity, for example an org or a product. This Flint is a Guide. See [[How to Ask This Guide]].

## The Member Flint

A Member Flint belongs to one person. It holds what that person keeps about one org. Its visibility is `private` and cannot be raised. The org cannot read it. The org of a Member Flint is never the org that it regards, and a Member Flint is never a member of a Tinderbox of that org. One person has one Member Flint per org.

## Commands

```bash
flint create <name> --type guide --about <address>   # a new Flint of a type
flint convert <flint> --to computer --dry-run        # plan a change of type
flint convert <flint> --to computer                  # apply it
```

A conversion never changes the id of the Flint. It checks the rules of the new type, writes the type, renames the folder, and runs the migrations of the type. A dry run prints the plan and changes nothing. The reverse direction works too.

## Where to go next

- [[Organisations and Visibility]] for what `private`, `org`, and `public` mean.
- [[The Tinderbox]] for how Flints group together.
