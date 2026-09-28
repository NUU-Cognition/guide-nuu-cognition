---
description: "Where each Flint command, core module, and error is in the Flint Public source copy, and how to search it"
---

# Knowledge: Flint Public Source Map

This file tells where things are in `Sources/Repos/Flint Public/`. Use it when the help text and the notes do not explain a behaviour or an error. All paths below are relative to that folder.

## What the Copy Is

- The copy is the Flint monorepo `NUU-Cognition/flint-public` (branch `main`). `flint sync` clones it without the `.git` folder.
- `.flint-receipt.json` in the copy records the source URL and the commit (`identity`). The marker `Mesh/Metadata/Sources/Repos/src-repo-flint_public.md` records the source repository in the Mesh.
- The copy can be older than the installed CLI. When the copy and `flint <command> --help` disagree, the installed CLI is correct for this machine.
- Example: on 2026-09-28 the copy held commit `128d5d0c` of 2026-09-05. That copy had no `flint fix` command and no staged six-step `flint setup` (`apps/flint-cli/src/commands/setup/stages.ts`). The installed CLI 0.7.0 had both.

## Top Level

| Path | What it holds |
|------|---------------|
| `apps/flint-cli/` | The `flint` CLI. `src/index.ts` is the entry. `src/commands/` holds one folder per group of commands. |
| `packages/flint/` | The core library: create, sync, the kernel, shards, Git, Obsidian, Tinderbox, rename. |
| `packages/flint-migrations/` | The migrations of a Flint (`flint migrate`). One file per step in `src/migrations/`. |
| `packages/flint-contracts/` | The shared types and the error codes for the server and the clients. |
| `packages/flint-server/` | The local Flint server (`flint server`). |
| `packages/orbh/`, `apps/orbh-cli/` | Orbh: agent sessions (`flint orbh`). `packages/orbh-*` are the harness adapters (Claude Code, Codex, and others). |
| `packages/orb*/` | Orb: the event store under Orbh. |
| `packages/blacksmith*/`, `apps/blacksmith-cli/` | Blacksmith: the daemon that starts the Flint servers and the Orbh orchestrator. |
| `apps/nuu-flint-plugin/` | The NUU Flint plugin for Obsidian. |
| `docs/` | Design notes. |

## Command to File

The commands are in `apps/flint-cli/src/commands/`. A command is declared as `new Command('<name>')`.

| Command | CLI file | Core code |
|---------|----------|-----------|
| `flint create` (`init`) | `flint/init.ts` | `packages/flint/src/create.ts` |
| `flint sync`, `flint plan` | `flint/sync.ts`, `flint/plan.ts` | `packages/flint/src/sync.ts`, `packages/flint/src/kernel/` |
| `flint doctor` | `flint/doctor.ts` | |
| `flint status` | `flint/status.ts` | |
| `flint move`, `rename`, `delete`, `open`, `cd`, `list`, `register`, `unregister`, `org`, `resolve`, `update` | `flint/<command>.ts` | `packages/flint/src/domain/rename.ts` (rename) |
| `flint shard ...` | `shard/` (`install.ts`, `start.ts`, `dev.ts`, `migrate.ts`, `registry.ts`, `inspect.ts`) | `packages/flint/src/domain/shards/` |
| `flint git ...` | `system/git.ts` | `packages/flint/src/domain/git/`, `packages/flint/src/domain/git-sync/` |
| `flint migrate` | `config/migrate.ts` | `packages/flint-migrations/src/` |
| `flint obsidian` | `config/obsidian.ts` | `packages/flint/src/obsidian/` |
| `flint config` | `config/config.ts` | |
| `flint setup` | `setup/setup.ts` | |
| `flint source` | `sources/source.ts` | |
| `flint workspace` | `workspace/workspace.ts` | |
| `flint reference`, `flint fulfill` | `references/` | |
| `flint tinderbox` | `agent/tinderbox.ts` | `packages/flint/src/domain/tinderbox/`, `packages/flint/src/domain/tinderbox.ts` |
| `flint orbh` | `agent/orbh.ts` | `apps/orbh-cli/`, `packages/orbh/` |
| `flint send` | `outputs/send.ts` | |
| `flint helper` | `system/helper/` | |
| `flint server` | `server/server.ts` | `packages/flint-server/` |

## Errors

- `packages/flint/src/shared/errors.ts` holds `FlintError` and the closed list `FLINT_ERROR_CODES` (for example `not_a_flint`, `invalid_state`, `conflict`, `git_error`). The CLI prints the `message` of the error as it is.
- Other domains have their own error classes. Find them with `grep -rn "class .*Error extends" --include="*.ts" packages apps`.
- `apps/flint-cli/src/command-kit.ts` prints the result lines of a command: the `✘` refusal, `Next:`, and `Or:`.

## How to Search

Run these commands from the root of the Guide. `rg` can be missing on a machine; `grep` is always present.

| Goal | Command |
|------|---------|
| Find an error text | `grep -rn -F "<text>" --include="*.ts" "Sources/Repos/Flint Public/apps" "Sources/Repos/Flint Public/packages" \| grep -v "\.test\.ts"` |
| Find a command | `grep -rn "new Command('<name>')" "Sources/Repos/Flint Public/apps/flint-cli/src"` |
| Find a flag | `grep -rn "'--<flag>" "Sources/Repos/Flint Public/apps/flint-cli/src"` |
| Find an error code | `grep -rn "'<code>'" --include="*.ts" "Sources/Repos/Flint Public/packages/flint/src"` |
| Find examples | Read the `*.test.ts` file beside the code file. |

Search for a distinctive part of a message. Leave out paths, names, and numbers, because the code builds them at run time.
