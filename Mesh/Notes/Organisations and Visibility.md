---
id: f0feba83-b33e-41fd-952f-496b9535a587
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# Organisations and Visibility

## What an org is

An organisation, or org, is an entity. It has an id, a Title, and a slug. The id is a UUID and is the truth. The slug is a short name, such as `my-org`, and is a cache. Every record that belongs to an org stores the org id, with the slug beside it for reading.

A person belongs to an org through a membership. A machine can be enrolled in an org. A Flint and a Tinderbox can carry the id of their org.

The public CLI has an `org` group:

```bash
nuu org create        # make a new organisation
nuu org invite        # invite a member
nuu org accept        # accept an invitation
nuu org members       # list the members
nuu org list          # list your organisations
nuu org select        # choose the active one
nuu org current       # show the active one
```

## Two orgs are compared by id

When two sides both hold an org id, the ids must be equal. A permission check needs an org id on both sides. It never reads the slug, because anyone can write a slug. A record with no org id gets no `org` permission.

## Three levels of visibility

A place, such as a Flint or a Tinderbox, has one visibility.

| Level | Who can read it through the network |
|---|---|
| `private` | Nobody. The place is not published and not reachable. It still works locally. |
| `org` | Machines of the same org, by id. |
| `public` | Any machine. |

The check runs before any policy check. A private place is refused before any other work. The check fails closed: when a record is damaged, partial, or newer than the reader understands, the place reads as `private`.

Each type of Flint has a default. A Guide is `public` by default. A Computer Flint is `private`. A Member Flint is `private` and locked, so it cannot be raised. See [[Typed Flints]].

## What an org can see

An org can read the places of its members that are `org` or `public`. It cannot read a `private` place. It can never read a Member Flint, even a Member Flint that regards it.

A read is not an action. To run something on another machine, such as the start of a session, a machine also needs a grant. See [[The NUU Network]].

## Where to go next

- [[Addresses]] for how an org appears in a name.
- [[The NUU Network]] for requests and grants.
