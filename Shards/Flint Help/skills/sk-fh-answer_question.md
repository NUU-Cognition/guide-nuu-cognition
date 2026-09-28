---
description: "Answer one question about Flint, with the commands, notes, and source files that give the answer"
---

> [!important] THIS FILE IS AN INSTRUCTION. WHEN REFERENCED IT IS MEANT TO BE TAKEN AS AN ACTION.

Run `flint shard start fh` if you haven't already.

# Skill: Answer a Flint Question

Answer one question about Flint. Use the evidence order of [[init-fh]] and name each source.

# Input

- The question of the person
- (Optional) Who asks: a new person, a developer, or an agent

# Actions

1. **Find the subject.** Find the Flint words in the question (Flint, Mesh, shard, source, lock, sync, Tinderbox, Orbh, org, address, and others). Read their lines in `Mesh/Notes/Glossary.md`.
2. **Ask the installed CLI.** When the question is about a command or a flag, run `flint --version` and `flint <command> --help`. The help text is the first source for the flags and the behaviour of this version.
3. **Read the note that fits.** Search `Mesh/Notes/` by file name first. Then search by text: `grep -ril "<word>" Mesh/Notes`.
4. **Read the shard knowledge.** When the notes are too short, read the knowledge files of `Shards/Flint/knowledge/` (for commands: `knw-f-cli.md`) and of `Shards/Orbh/knowledge/` (for agent sessions).
5. **Read the source code.** When the help, the notes, and the knowledge do not explain the behaviour, use [[knw-fh-source_map]] to find the file. Search the code without the tests first:

   ```bash
   grep -rn -F "<text>" --include="*.ts" "Sources/Repos/Flint Public/apps/flint-cli/src" "Sources/Repos/Flint Public/packages/flint/src" | grep -v "\.test\.ts"
   ```

   Read the function around each hit. A `*.test.ts` file beside the code shows examples of the behaviour.
6. **Compare the rungs.** When the source and the installed CLI disagree, the installed CLI wins. Tell the person that the source copy is older than the CLI.
7. **Write the answer.**
   - Start with the direct answer in one to three sentences.
   - Then give the details and one example command, when it helps.
   - End with a `Sources:` list: each command, note, and file that you used.
   - Match the level of the person. For a new person, explain each Flint word.
8. **Say when there is no answer.** When no rung answers, write: "This Guide and the Flint source do not answer this." Then name the public site that can.

# Output

- One answer with its sources
- No change to any file
