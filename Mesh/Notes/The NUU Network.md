---
id: 8f81d686-16f3-4263-9b28-b3ba51193953
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# The NUU Network

The NUU Network lets the machines of a person or an org find each other's Flints, read them when visibility allows, and run a small set of actions on each other with permission. This note stays at a high level.

## One client per machine

Each machine runs one NUU client, called nclient. It is a small daemon that listens on the local machine only. It does four jobs:

1. It holds a table of the places on this machine: the Flints, the Tinderboxes, and their roots.
2. It routes an entity request to exactly one place.
3. It checks the local policy before every send.
4. It links this machine to other machines through NUU Network, a hosted service.

A machine joins the network with `nuu client enroll`. It stores a token for itself. A machine can leave with `nuu client forget`. A machine removes only itself.

```bash
nuu client start     # start the daemon in the background
nuu client status    # is it running, and for which machine
nuu client stop      # ask it to stop
```

## Requests

Every request has one id, called the trace id. The id stays the same for the whole life of the request. Every machine that touches the request writes the id in its log. So a person or an agent can trace one request across machines.

A request has a verb. The verbs form levels:

| Level | Verbs | Meaning |
|---|---|---|
| L0 | `describe`, `lookup` | What is this entity? |
| L1 | `locate`, `children` | Where is it? What is inside it? |
| L2 | `rename`, `rewriteReferences` | Local changes. Never across machines. |
| L2b | `invoke` | Run an action. Needs a grant between machines. |
| L3 | `reach`, `fetch`, `watch` | Live contact. |

A response has a state, such as `resolved`, `denied`, or `unreachable`. A `denied` response always gives a reason. Every response names who answered and what it passed through.

## Visibility first, then policy

Before any policy check, the client applies visibility. A `private` place is never published and never answered from the network. An `org` place answers only a machine of the same org, by id. See [[Organisations and Visibility]].

## Grants

An `invoke` between machines needs a grant. A grant lets another machine run one action on this machine. It writes a local policy rule and a server record. The owner of the target machine gives it, and can remove it.

```bash
nuu net grant     # let another machine run an action on this machine
nuu net revoke    # remove that grant
nuu net grants    # list grants where this machine is the target or the subject
nuu net machines  # list the machines of your owner
```

The actions of `invoke` are:

- `session.start`: start a headless Orbh session in a Flint, and get back its address.
- `station.send`: put one item in the queue of a station in a Flint.
- `session.transfer`: move a saved session to a Flint on another machine, so it can resume there. The source is never deleted.

## Where to go next

- [[Addresses]] for the names that a request targets.
- [[Agents and Orbh Sessions]] for the sessions that the network starts.
