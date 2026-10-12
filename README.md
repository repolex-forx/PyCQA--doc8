# Repolex Knowledge Graph of PyCQA/doc8

RDF knowledge graph data for [PyCQA/doc8](https://github.com/PyCQA/doc8), parsed by [repolex](https://repolex.ai).

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
rlex download PyCQA/doc8
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e4d2539177a3d72c8e52d91708bbe62e5085155d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e4d2539177a3d72c8e52d91708bbe62e5085155d
│           └── chunk-001.nq.gz
├── blob
│   ├── 029b3a8c6d6d494720068701c7be3dc5b9dc8f14.nq.gz
│   ├── 0709f9a46155b2f6c92b4dc98de324e7b35aff28.nq.gz
│   ├── 08e6b874693aeef8f6ab329476d9b507f57e14ad.nq.gz
│   ├── 1053bd62b25a9993a81a285457ac841c69fd7f3e.nq.gz
│   ├── 14650b492194e11085b9661c486f401956e89887.nq.gz
│   ├── 155c1ff893f01732a028016eca9507fbd03c03ab.nq.gz
│   ├── 1728a61ca25fd9c25280aa71414fa86b48c73444.nq.gz
│   ├── 28baac9b5917e7d14056ff2a6166c51985c0e910.nq.gz
│   ├── 2b6870f619be0aba06ff79e2a23812ff38ba1cc9.nq.gz
│   ├── 34667d0b04c2601ced0ebd451eb10feb2ce1df8d.nq.gz
│   ├── 473c22a8e0143a32d16a54e57be00bce490a3e4b.nq.gz
│   ├── 52f8cf295d1cc11c2561d9e2610d77a478131864.nq.gz
│   ├── 5c304d1a4a7b439f767990bf1360d3283e45d0ee.nq.gz
│   ├── 68313f5173ace5e000cbf16281572c5be1c4f45a.nq.gz
│   ├── 7664544bec2189671b1192cfe24727163b9d9591.nq.gz
│   ├── 86684ff98cd7d4503fafc68ffb5370c566a69ed0.nq.gz
│   ├── 8b34dba17b7a38668649a208feaedc92c94e2ae5.nq.gz
│   ├── 94bdea9d945caefc0aad94716604725f7618c05b.nq.gz
│   ├── 9606976f9bb38bb783b0cf233223c493d2a913b8.nq.gz
│   ├── a27605a8eeaa3d5374f18ffbda3a5d7298375a8a.nq.gz
│   ├── a6210d3d8a7988fdee6556eeba665d6b58ee6db4.nq.gz
│   ├── a95054a1fd24f082bb8b8f20b0c07545d7a521fb.nq.gz
│   ├── abaecd3c52795628fa19a2307f24a8d4522b081d.nq.gz
│   ├── b0d8019fd8d45a4d9751ce0130b33b78bf99cf8e.nq.gz
│   ├── b2c18a90c2e9878cbb90a95f8e4fa6a87ca103be.nq.gz
│   ├── b531cbd3d0c18818488e4e5846eff1e42cf34c0a.nq.gz
│   ├── ca0a41e4fc66805902899001f17d0f373fb08bb0.nq.gz
│   ├── cb6ad0e423a6371c66815b4972318428bcfe4bd1.nq.gz
│   ├── ccb3a37e128c414d5920122bef7bd05b2b3b9fae.nq.gz
│   ├── d142b4d42abefed5bc156f3b4e7dc859b7ece3e8.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ecfdea5edd21d85f87cd4151921454451b002b9b.nq.gz
│   ├── f12a60acaf802d39df1aa93225a46113a9f2d716.nq.gz
│   ├── f5a7de76863c27a01c3beb61153791a66553aba1.nq.gz
│   ├── f5c33038febf01e161ab84ceab75b2ec9f38d824.nq.gz
│   ├── f6abbd3ec409bda2ae950a46d5ab0c9f852eecff.nq.gz
│   ├── f7e3fd94613390fce57fea62032388f8b6804364.nq.gz
│   ├── feb8cb65afcead2f00f708c583070d5db3477899.nq.gz
│   └── ff4f050a53c0633c5063ee91b41a41b6aec548af.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e4d2539177a3d72c8e52d91708bbe62e5085155d.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 47 files
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

[PyCQA/doc8](https://github.com/PyCQA/doc8)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
