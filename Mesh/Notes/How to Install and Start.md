---
id: 3a3d3e43-e46a-41f5-a05b-2a32372a85a0
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# How to Install and Start

This note gives the first steps on a new machine. Check the Flint site, `flint.nuucognition.com`, for the current install instructions. Access can be limited before the public launch.

## What you need

- Node.js 20 or newer.
- A terminal agent, such as Claude Code or Codex.
- Obsidian, optional. A Flint is plain markdown, so any editor works.

## Install the CLI

```bash
npm i -g @nuucognition/flint-cli
```

This gives you the `flint` command.

## Set up the machine

```bash
flint setup
```

Setup asks for your Name. The Name is the operator identity of every Flint on this machine. It is stored once, machine-wide, in your home directory. Setup can also install a shell integration for Flint and Orbh.

```bash
flint whoami          # show your Name and machine name
```

## Make a Flint

```bash
flint init "My Notes"                 # a plain Flint in the current directory
flint init "My Notes" --preset lab    # with a preset shard list
flint init "My Notes" --no-open       # do not open Obsidian
```

`flint init` creates the standard folders, `Mesh/`, `Media/`, and `Shards/`, and registers the Flint on the machine. Newer builds also offer `flint create`, which adds `--type`, `--org`, and `--visibility`. See [[Typed Flints]].

## Add capabilities

```bash
flint shard list
flint shard install <owner/repo>
```

See [[Shards]] and the registry at `shards.nuucognition.com`.

## Start an agent

Open a terminal in the Flint root. Start your agent there. Tell it to read `Mesh/(System) Flint Init.md` first, then to run `flint shard start f` and follow the required readings. From then on, the agent knows the rules of the workspace.

## Use this Guide

1. Clone this Guide with git.
2. Open a terminal in its root.
3. Start your agent and ask a question. See [[How to Ask This Guide]].

## Join a network

The network is optional. When you want your machines to see each other's Flints:

```bash
nuu client enroll     # join NUU Network with this machine
nuu client start      # start the local client
```

See [[The NUU Network]].

## Where to go next

- [[What a Flint Is]] for what you just made.
- [[The Mesh]] for where to write.
