---
id: 5d0cd52f-f2fb-4add-9022-dd9805137a6e
tags:
  - "#guide/nuu-cognition"
  - "#note"
authors:
  - "[[@NUS]]"
orbh-sessions:
  - "[[2ff5aec8-2ffa-412b-b5fc-88b569465d70]]"
---

# The Other Products

NUU Cognition builds a stack of products. Flint and Shards have their own notes. This note gives one paragraph on each of the others. Only products that the public docs describe are here.

## Mesh

Mesh is the data structure under the whole ecosystem: markdown documents and media blobs that reference each other with wikilinks. It normalises data into a flat namespace with indexes for links, backlinks, tags, and types. It is fractal and storage-agnostic. A Mesh can be one file or a whole knowledge base. See [[The Mesh]]. Site: `mesh.nuucognition.com`.

## NUU Cognition Markdown (NCM)

NCM is a flavour of markdown, with its parser, that treats a document as a series of blocks. Extra syntax lets a person define custom blocks in plain text, so markdown can represent more complex structures. Obsidian adds a few components to markdown. NCM opens that door for any future addition. Vessel uses NCM to parse and display content. Site: `ncm.nuucognition.com`.

## Vessel

Vessel publishes a Mesh to the web. It is like Obsidian Publish, but a declarative YAML file maps your markdown files to a wider range of frontends. Vessel arranges and publishes a subset of a Mesh. Flint is the editor; Vessel is the publisher. Site: `vessel.nuucognition.com`.

## Surf

Surf is a zoomable reading interface, like a map for your documents. It builds summaries at several levels of abstraction and lets you zoom in and out. It is a direct example of a thinking technology, because it changes how you engage with information. It is in development.

## Parse

Parse is the ingestion engine. It takes an external file, such as a PDF, an audio recording, or a web page, and turns it into a Mesh, not only into flat markdown. It runs as a pipeline of steps: OCR, cleaning, structure identification, and Mesh construction. New file types are supported by new steps.

## NUU Docs

NUU Docs is the source library. It accepts an artifact from the outside world and turns it into structured NCM. An ingested document becomes an immutable reference, a "golden master". You can quote it, link to it, and transclude it, and it stays fixed. The Mesh is the workshop; NUU Docs is the library. Parse is the engine under it.

## OrbCode

OrbCode is cognitive programming for codebases. It keeps a human-readable semantic layer of model notes on top of a codebase, verified by a test layer under it. Work runs in a stability cycle: write the spec, write failing tests, implement, verify, and return to stable. It was the first cognitive program in the ecosystem, and it runs as a shard inside a Flint.

## NUU University

NUU University is a peer-to-peer learning and research protocol. There are no professors, grades, or certificates. Practitioners publish what they learned as a Mesh. The community validates by use. Learning materials are Mesh-native, so they can be read in Surf and published through Vessel.

## Orbh

Orbh is local headless agent orchestration. See [[Agents and Orbh Sessions]].

## Where to go next

- [[What NUU Cognition Is]] for how the products connect.
- [[How to Install and Start]] for the first tool to try.
