---
id: 2c776ded-34d4-4275-8174-995814620d75
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# The Mesh

A Mesh is any collection of markdown documents and media blobs, from one file to a whole knowledge base. Documents reference each other with `[[wikilinks]]`. Media files are embedded with `![[target]]`. Mesh is the data structure that Obsidian works on, made explicit and standard. It is a cognitive data primitive for humans, language models, and machines.

Inside a Flint, the Mesh is the content layer: everything under `Mesh/` and `Media/`. Flint is a Mesh editor. Vessel is a Mesh publisher. See [[The Other Products]].

## The Mesh is flat

Every document has a globally unique title. The folder it sits in is display only. Structure lives in the frontmatter, not in the folders. A Mesh normalises its data into a flat namespace with indexes for links, backlinks, tags, and types.

## Frontmatter

Every document starts with YAML frontmatter. Two fields are required.

```yaml
---
id: 7b1c3d0e-2f4a-4b6c-8d9e-0f1a2b3c4d5e
tags:
  - "#note"
---
```

`id` is a permanent identifier. It never changes, even when the title changes. `tags` classify the document. Tags are quoted, because `#` starts a YAML comment. Common optional fields are `status`, `authors`, `template`, and `orbh-sessions`.

## Notes and typed artifacts

A **note** is the base unit of free content. It holds one editable model per file. It has no type prefix in its name. Its title stands alone and describes its content. See [[Models and Information Environments]].

A **typed artifact** follows a template that a shard defines. Its name has the pattern `(Type) NNN Name.md`, for example `(Task) 042 Write the guide.md`. Typed artifacts live under `Mesh/Types/<Type>s/`. Finished ones move to `Mesh/Archive/`.

A **dashboard**, `(Dashboard) Backlog.md` for example, is a live view that aggregates artifacts.

## Sections and groups

Two tags give a flat Mesh its structure.

- `#ie/sections/<name>` says where a note lives. Exactly one per note.
- `#ie/groups/<name>` says which collections a note is part of. Any number.

A Flint has three staging sections under `Mesh/Main/`: New, Working, and Consolidated. A note with no destination lands in New. Processing moves it forward.

## Where to go next

- [[Shards]] for the programs that read and write the Mesh.
- [[What a Flint Is]] for the workspace around it.
- `mesh.nuucognition.com` for the Mesh product.
