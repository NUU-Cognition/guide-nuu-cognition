---
description: "Frequent Flint problems: the text that the CLI prints, the cause, and the next command"
---

# Knowledge: Common Flint Problems

This file lists frequent Flint problems. Each row gives the text that the CLI prints, the cause, and the next command. The texts come from Flint 0.7.0. A newer CLI can print other words, so match a row by its meaning. The `Next:` line of the real output always wins over this file.

## How Flint Reports a Failure

- A refusal starts with `✘`. The lines `Next:` and `Or:` give the commands that fix it.
- When `flint sync`, `flint create`, `flint git sync`, `flint shard install`, `flint setup`, or `flint tinderbox sync` fails, Flint writes a failure record and prints `Or: flint fix`. The record is a JSON file in `~/.nuucognition/flint/failures/`. `flint fix --list` lists the records, the newest first.
- `flint fix` starts a repair session: an agent that reads the failure record and repairs with the person.
- `flint doctor` checks the machine and the current Flint. It gives one `Next:` command for each failed check. It starts no agent.
- Exit code 2 means blocked: the command stopped before it changed anything. Exit code 1 means failed.

## The Flint and Its Version

| Text (by meaning) | Cause | Next |
|-------------------|-------|------|
| `not a Flint`, `not_a_flint` | The command ran outside a Flint. A Flint is a folder with `flint.toml`. | `cd` into the Flint, or add `-p <dir>`, or run `flint cd "<name>"`. |
| `This Flint has the 0.6.0 shard records`, `is not at the current Flint Version`, `shard records are in the legacy shape` | An older CLI made the Flint. | `flint migrate run --dry-run` to see the plan, then `flint migrate run`. The run prints a rollback command. |
| `flint.toml` does not parse (exit 2) | A syntax error in `flint.toml`. | Correct the file, then run `flint sync`. |
| `Upgrade flint-cli` | The Flint has a record of a newer shape than this CLI reads. | `flint update`. |
| No Name, or no Git author | The machine is not set up. | `flint setup`. To change the Name only: `flint config name "<Name>"`. |

## Obsidian

| Text (by meaning) | Cause | Next |
|-------------------|-------|------|
| `.obsidian in <name> is a legacy Git payload` | The Flint has the old Obsidian files of Flint 0.6. | Close the vault in Obsidian. Then run `flint migrate run`. |
| The install waits (a pending install), or `Obsidian runs, so the vault registry change waits` | Obsidian has the vault open. | Close the Flint in Obsidian. Then run `flint open "<name>"`, or `flint obsidian vaults repair --yes` with Obsidian quit. |
| A release file changed outside Flint (exit 2) | A person edited a Flint file in `.obsidian/`. | `flint obsidian repair --replace --dry-run` to see the change. Then run it without `--dry-run`. |
| "Vault not found" at the first open | The vault registry of Obsidian has no entry for the folder. | In Obsidian, use "Open folder as vault". Later, `flint open "<name>"` works. |

## Shards

| Text (by meaning) | Cause | Next |
|-------------------|-------|------|
| `The shard <a> needs <b>, which is not present in this Flint` | A dependency of a shard is missing. | The command on the `→` line, for example `flint shard install NUU-Cognition/shard-invironments`. |
| `not-locked` | `flint.toml` declares a shard that the lock does not hold. | `flint shard install`. |
| `The build of <alias> is stale` | The source of the shard changed after its build. | `flint shard build <alias>`. |
| `FORCE SETUP`, `SETUP REQUIRED` at `flint shard start` | The shard needs its one-time setup. | Follow the setup file that the output names. Then run `flint shard setup <alias> --complete`. |
| Shard migrations pending at `flint shard start` | A new version of the shard has migration steps. | `flint shard migrate run <alias>`. |
| `ambiguous` | The ref names two shards. | Use one of the aliases that the output names. |
| `id-mismatch` | A person wrote an `id` in `flint.toml` that differs from the lock. | Remove the `id` from the record in `flint.toml`. |
| `The registry did not answer. The answers were not recorded.` | No network, or the shard registry is down. | Nothing is broken. Run `flint shard install` later to record the answers. |

## Git

| Text (by meaning) | Cause | Next |
|-------------------|-------|------|
| `flint git sync` stops on a conflict (exit 2) | Local and remote changes touch the same lines. | Resolve the files, then `flint git sync --continue`. Or take one side: `flint git resolve --local <paths>` or `--remote <paths>`. To stop: `flint git sync --abort`. |
| A held merge, cherry-pick, or revert refuses `sync` (exit 2) | Git has an operation that is not finished. | `git <kind> --continue` or `git <kind> --abort`. Then run the command again. |
| `Local history is N commits ahead of origin` | Local commits are not pushed. | `flint git sync`. |
| The remote history was rewritten | Someone force-pushed origin. | `flint git sync --replay`. |
| The wait for the run lock timed out (`blocked`, exit 2) | Another Git run of Flint holds the lock of the repository. | Wait until the other run ends. Then run the command again. |
| `flint git publish` refuses: not the root of a repository | The Flint has no Git repository. | `flint git init`. Then run `flint git publish <url>` again. |

## Commands in an Agent or a Script

| Text (by meaning) | Cause | Next |
|-------------------|-------|------|
| `It needs a confirmation, and this terminal cannot ask. Nothing was written.` | The command needs a yes, and the terminal is not interactive. | Read what the command changes. When the person agrees, run the command on the `Next:` line (it adds `--force` or `--yes`). |
