# Flint Help

Answers any question about Flint and explains any Flint problem, from the installed CLI, the guide notes, and the Flint Public source code.

This folder is the local source of the Flint Help shard (shorthand `fh`). Edit the files here. Then run `flint shard build flint-help` to build the shard in `Shards/Flint Help/`.

## Use

Start an agent in the root of the Guide and load the shard with `flint shard start fh`. Then ask a Flint question, or paste the full output of a Flint command that failed.

## Files

| File | Purpose |
|------|---------|
| `dev-init-fh.md` | The evidence order and the rules |
| `skills/dev-sk-fh-answer_question.md` | Answer one Flint question with sources |
| `skills/dev-sk-fh-explain_problem.md` | Explain a Flint problem and give the next command |
| `knowledge/dev-knw-fh-source_map.md` | Where each command and error is in `Sources/Repos/Flint Public` |
| `knowledge/dev-knw-fh-common_problems.md` | Frequent problems, their causes, and their next commands |

The shard reads the source repository `Flint Public` (`https://github.com/NUU-Cognition/flint-public`). `flint sync` clones it into `Sources/Repos/Flint Public/`.
