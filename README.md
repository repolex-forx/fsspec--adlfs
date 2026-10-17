# Repolex Knowledge Graph of fsspec/adlfs

RDF knowledge graph data for [fsspec/adlfs](https://github.com/fsspec/adlfs), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download fsspec/adlfs
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6362b4f2e25698cac84dafc64aa038052b82aa7b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6362b4f2e25698cac84dafc64aa038052b82aa7b
│           └── chunk-001.nq.gz
├── blob
│   ├── 04fed0020fac54b82006486c8ad74044a08d47a6.nq.gz
│   ├── 051ed1e8dbc41ed80b9f2ee0408e920a61addf44.nq.gz
│   ├── 09f1a3f243a2b2613c0fcd5f80a5e9f6cf03abc6.nq.gz
│   ├── 153be5e2f6f996741b53558d8bc7825ec091699c.nq.gz
│   ├── 1c11ae92bd0cc077d6b1ffb77e71222fa05986bb.nq.gz
│   ├── 1d2d923b96da4cf9ea2674c5b5495dee47e97529.nq.gz
│   ├── 20a34c1f8dab7a9c999cbd24f978726325b5733b.nq.gz
│   ├── 258ff6344c2db537c20a2d6c5ae6fb51f29bc865.nq.gz
│   ├── 2c59b21367fa033c1202bc4acb9c9815240eadb4.nq.gz
│   ├── 302a51d9201cc9fa950d46a917f0e05208271bc5.nq.gz
│   ├── 309dd82351b9dd1bfb3a96ec75ca2b3a0ebe5ab2.nq.gz
│   ├── 31b92d19c86424267dd68cca5d3fc32ead902ce1.nq.gz
│   ├── 403fc9dd7347ad721a9733225e6bbb97deb6e01e.nq.gz
│   ├── 456f84bc90db6fb880c2da88bdf0b5742a298a2f.nq.gz
│   ├── 4b05db6cd99ea2ca87175d603cbc8d1ecc3af126.nq.gz
│   ├── 4d9c8fbf26a98ae5f0c9c9f28965b530134bedfc.nq.gz
│   ├── 550309d281612de8e631c36a6cbad64959694210.nq.gz
│   ├── 5f42ef03ccb66c9804b758b6a6024e79281b2b89.nq.gz
│   ├── 5f68378a2bc5f7d190783797314a379ad9bc2fe3.nq.gz
│   ├── 690781e5df8d84b124f9ab725a9db98a3a547638.nq.gz
│   ├── 7146dc17851c10578027af142431fcfa8263b451.nq.gz
│   ├── 832b98a58c979485b768e4c811234eaba4ba0062.nq.gz
│   ├── 86154cbfd3d983480c8e5c52b02a8c615f6e042d.nq.gz
│   ├── 8a4aa14de9bd76016354a0317d889d2d08af2713.nq.gz
│   ├── 8e29084b537d75f2e0fa2351b84e2825c6d417f1.nq.gz
│   ├── 9332a4ab587ddc466d5d406e1805ec80bfd90e08.nq.gz
│   ├── 93d0b6c0e3d25469a23e004342468851c499fffa.nq.gz
│   ├── 96b163f659fa2b5bd8963d4b1d6aa812e85cc14d.nq.gz
│   ├── c47cdbb926f09d2ea4959be56fae2ac0fdd543f0.nq.gz
│   ├── c79dda7ce5d4218caa9ab65538dbd0ed9e9f68d7.nq.gz
│   ├── c7e6ca9067518e06e62783c7d43552e66fcf230a.nq.gz
│   ├── cf4a968a5b370fc8af6e91266cc42e1022819a95.nq.gz
│   ├── d3edf0e11b5b089afe98a8b4c1bae7fc8ac94e6a.nq.gz
│   ├── d4bb2cbb9eddb1bb1b4f366623044af8e4830919.nq.gz
│   ├── dece0b81dd5ab916ec2543e68a67937990d18ea0.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── e8e65801e50afc4d33d049a26f5afdb60b6d8980.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6362b4f2e25698cac84dafc64aa038052b82aa7b.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 45 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[fsspec/adlfs](https://github.com/fsspec/adlfs)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
