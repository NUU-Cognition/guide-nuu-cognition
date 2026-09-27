---
id: c0c7d7c6-9f88-43b7-8fd0-06cb0001626c
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# Agents and Orbh Sessions

## An agent in a Flint

A terminal agent, such as Claude Code or Codex, runs inside a Flint. Its working directory is the Flint root. It can read and write files, run shell commands, and search code.

An agent session is stateless. Each conversation starts fresh. The Flint is the memory. So an agent follows a fixed routine:

1. Read `Mesh/(System) Flint Init.md` first. It says what the Flint is about and what is installed.
2. Load a shard before using it. See [[Shards]].
3. Read before writing. Follow the existing naming and tag conventions.
4. Write all outputs into `Mesh/`.
5. Record its session id in the `orbh-sessions` field of every artifact that it creates or changes. Record the person as the author.

## Interactive and headless

An agent can run interactive, with a person at the terminal. It can also run headless, with no terminal, managed by Orbh. In headless mode the agent loads the headless init of a shard, `hinit-<sh>.md`, when one exists, and prefers headless workflows that drop the human review gates.

## What Orbh is

Orbh is local headless agent orchestration. It launches, observes, and records agent sessions. Sessions move through queued, running, completed, suspended, or failed states. Every runtime maps to the same structured transcript format. Runtime adapters exist for Claude Code, Codex CLI, and custom agents.

Orbh is a durable session layer. A session has a stable id, a title, a description, and a set of key and value pairs that show its progress. A session runs interactive, headless, or as a subagent.

## Turns and results

A headless run is one turn. Every turn ends with an explicit return: `finish` when the work is done, or `await` when the session expects more interaction. A collector waits for the result of the turn that it dispatched. A session can return many results over its life.

## Delegation

A session can dispatch subagents. Each subagent is one node in a delegation tree. The child shares no context with the parent, so the parent gives it a complete prompt. A session can also launch a peer, which no collector waits for. Sessions talk through messages and through rooms. A room is a shared channel with a message stream and a context library.

Orbh sessions in a Flint can also have an address on the network, so a session can be started on another machine. See [[The NUU Network]].

## Where to go next

- [[Shards]] for the programs an agent runs.
- [[How to Ask This Guide]] for how to use an agent with this Guide.
