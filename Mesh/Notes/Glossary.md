---
id: 536505af-9c74-40c2-802e-24c268f6d0bc
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# Glossary

One line per term. Follow the link for more.

- **Address.** A way to point at an entity: `@org/type/name`, `@<uuid>`, or a relative path. See [[Addresses]].
- **Agent.** A terminal AI program, such as Claude Code or Codex, that works inside a Flint. See [[Agents and Orbh Sessions]].
- **Artifact.** A markdown document in the Mesh with frontmatter. Typed artifacts follow a template.
- **Computer Flint.** The one Flint that models one machine. Private. See [[Typed Flints]].
- **Cognitive program.** Instructions that an agent executes against information. A shard is one.
- **Entity.** Any thing with a type, an id, and a name: a Flint, a machine, a person, an org.
- **Flint.** A workspace directory with `Mesh/`, `Media/`, and `Shards/`, managed by the Flint CLI. See [[What a Flint Is]].
- **Grant.** Permission for one machine to run one action on another machine. See [[The NUU Network]].
- **Guide.** A public Flint that a person clones and asks questions of. This Flint is one.
- **Id.** A UUID that identifies an entity for its whole life. It never changes.
- **Information Environment (IE).** A mind, or a context like a mind, in which a model has meaning. See [[Models and Information Environments]].
- **Member Flint.** The private Flint of one person about one org. Its visibility cannot be raised.
- **Mesh.** A collection of markdown documents and media that link to each other. The content layer of a Flint. See [[The Mesh]].
- **Model.** A representation of some part of reality, built by a mind. Everything in a Flint is a model.
- **Model note.** One note that holds one model of one thing. The atomic unit of the Mesh.
- **nclient.** The one NUU client that runs on each machine. It routes requests and links to the network.
- **NCM.** NUU Cognition Markdown, a flavour of markdown made of blocks. See [[The Other Products]].
- **Note.** The base unit of free content in a Mesh. No type prefix in its name.
- **Orbh.** Local headless agent orchestration: launch, observe, and record agent sessions.
- **Org.** An organisation, an entity with an id and a slug. See [[Organisations and Visibility]].
- **Place.** A thing on a machine that can answer a request: a Flint, a Tinderbox, or a root.
- **Preset.** The shard list of a new Flint, such as `lab` or `library`. Not a type.
- **Section.** Where a note lives in the Mesh, set by one `#ie/sections/<name>` tag.
- **Session.** One managed run of an agent, with a stable id, under Orbh.
- **Shard.** A cognitive program that extends an agent inside a Flint. See [[Shards]].
- **Station.** An addressable queue inside a Flint that another machine can send an item to.
- **Thinking technology.** A tool that helps a mind build, share, and use models of reality. See [[Thinking Technologies]].
- **Tinderbox.** A directory that holds many Flints and shared repos as one declared unit. See [[The Tinderbox]].
- **Trace id.** The one id of a request that appears in every log line on every machine that touched it.
- **Type.** What a Flint is for: `flint`, `computer`, `guide`, or `member`.
- **Vessel.** The product that publishes a Mesh to the web.
- **Visibility.** `private`, `org`, or `public`. Who can read a place through the network.
- **Wikilink.** `[[Title]]`, a link from one document to another by title.
