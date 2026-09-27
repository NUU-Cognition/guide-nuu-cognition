---
id: 5f6afcd4-0e40-451e-8c71-cc891e659505
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# Addresses

Every thing in the NUU ecosystem is an entity. An entity has a type, an id, and a name. The id is a UUID. It never changes. The name can change. An address is how you point at an entity.

Entity types include: a Flint, a shard, a Mesh, a Mesh document, a blob, a session, a run, a machine, a person, an org, a repo, a published Mesh, a Tinderbox, and a station.

## Three forms

| Form | Shape | Resolves |
|---|---|---|
| Scoped | `@org/type/name` | Inside the named org |
| Absolute | `@<uuid>` or `@<short-id>` | From anywhere |
| Relative | `type/name` or a bare `name` | In the nearest scope |

A scoped address is a path of type and name pairs. Examples:

```
@my-org/flint/my-notes                    a Flint named "my-notes" in the org "my-org"
@my-org/flint.guide/my-guide              a Guide; the type of the Flint is its subtype
@my-org/flint/my-notes/station/inbox      a station inside a Flint
@7b1c3d0e-2f4a-4b6c-8d9e-0f1a2b3c4d5e     the same thing by id, from anywhere
```

A pair with no subtype, such as `flint/my-notes`, matches a Flint of every type. So the same address finds a Flint before and after a change of type. A preset never appears in an address. See [[Typed Flints]].

## Name segments

A name segment has one of four kinds.

- **Title.** A lowercase slug in kebab case, `my-notes`.
- **Ordinal.** A number such as `3` or `3.16.0`.
- **Id.** A full UUID.
- **Short id.** The first eight or more characters of a UUID, in hexadecimal.

## Relations

An entity can point at other entities. A Computer Flint has `of`, the machine. A Member Flint has `owner`, the person, and `regarding`, the org. A Guide has `about`. A Flint in a Tinderbox has `memberOf`. Each relation holds the id as the truth and an address as a cache.

## Resolving an address

A resolution finds where an entity is. The result has a state: `resolved`, `moved`, `broken`, `unreachable`, `unsupported`, or `denied`. A `moved` result gives the new location. A `denied` result gives a reason. The command `nuu resolve <address>` asks the local client. See [[The NUU Network]].

## Where to go next

- [[Organisations and Visibility]] for the `@org` part.
- [[The NUU Network]] for what happens when an address is on another machine.
