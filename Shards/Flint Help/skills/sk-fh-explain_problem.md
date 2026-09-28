---
description: "Explain why a Flint command failed or did an unexpected thing, and give the next command"
---

> [!important] THIS FILE IS AN INSTRUCTION. WHEN REFERENCED IT IS MEANT TO BE TAKEN AS AN ACTION.

Run `flint shard start fh` if you haven't already.

# Skill: Explain a Flint Problem

Find why a Flint command failed, or why it did not do what the person expected. Explain the cause with evidence, and give the next command.

# Input

- The command that the person ran, or a description of the problem
- (Optional) The output of the command

# Actions

1. **Collect the facts.** Ask the person for each fact that is missing. Do not guess.
   - The exact command, and the folder where it ran.
   - The full output. A part of the output is not sufficient: a refusal or a `Next:` line can be on any line.
   - The exit code (`echo $?` just after the command).
   - What the person expected.
2. **Collect the state of the machine.** Run these read commands:
   - `flint --version` and `flint status`.
   - `flint doctor`. For another Flint, run `flint doctor -p <dir>`.
   - `flint fix --list`. Read the newest failure record (a JSON file). Its fields `code`, `reason`, `next`, and `stderrTail` hold the failure.
   - For a problem in one Flint: `flint sync --dry-run` in that Flint.
   - For a Git problem: `git status` and `git log --oneline -5` in that Flint.
3. **Match a known problem.** Read [[knw-fh-common_problems]]. Match by the meaning of the text, not by exact words, because a newer CLI can print other words. When a row matches, use its cause and its next command.
4. **Find the text in the source.** When no row matches, take a distinctive part of the error text. Leave out paths and names. Search:

   ```bash
   grep -rn -F "<text>" --include="*.ts" "Sources/Repos/Flint Public/apps" "Sources/Repos/Flint Public/packages" | grep -v "\.test\.ts"
   ```

   Read the function around each hit: the condition that stops the command, the error code, and the next command that it prints. [[knw-fh-source_map]] tells where each command lives. When the text is not in the source copy, the installed CLI is newer than the copy. Say so, and use the CLI output and `--help`.
5. **Write the explanation** in this form:
   - **What happened:** one or two sentences, with the error text quoted.
   - **Why:** the cause, with the file, the note, or the command output that shows it.
   - **Next:** the exact commands, in order. Mark each command that writes.
   - **If that does not work:** `flint fix` starts a repair session with the failure record. For a bug in Flint, list the evidence for a bug report (see [[init-fh]] § Rules).
6. **Run a fix only with agreement.** Ask the person before each command that writes. After the fix, run the check again (`flint doctor`, `flint sync --dry-run`, or the first command) and report the result.

# Output

- An explanation with the cause, the evidence, and the next commands
- Changes to files only when the person agreed to them
