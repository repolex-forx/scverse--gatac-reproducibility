# Repolex Knowledge Graph of scverse/gatac-reproducibility

RDF knowledge graph data for [scverse/gatac-reproducibility](https://github.com/scverse/gatac-reproducibility), parsed by [repolex](https://repolex.ai).

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
rlex download scverse/gatac-reproducibility
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 834b0bf8af344c8850d408874214955550474b40
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 834b0bf8af344c8850d408874214955550474b40
│           └── chunk-001.nq.gz
├── blob
│   ├── 015d248dfefc774c8ffa687fa9006e2d8903f88e.nq.gz
│   ├── 03ab282b9736acdfe83c0311f1a107cdf1b24f34.nq.gz
│   ├── 09a78b9c1cb102b8417351c952bf0a29008fcd9d.nq.gz
│   ├── 18f8ac63a35600941c1aaf40963ec484f1225e10.nq.gz
│   ├── 1efbc789d3ecc131f4a2d3cdae8a65d05e5af2ec.nq.gz
│   ├── 2027d15e8aad8210d97e14951003488a22496965.nq.gz
│   ├── 20adf38c464a66f34b6d28a81eceea1faeb6597f.nq.gz
│   ├── 2436fc8fbacdcb18bd427cd082c15b0803b6d074.nq.gz
│   ├── 295f3b31b8019820e1f42d159d7171f6fe01ef16.nq.gz
│   ├── 299690b1c4e8d8c9bc6e40b054ba1d3b6e6861c9.nq.gz
│   ├── 2a93a871bd90aea638aff6c06ba5e1dd783d2c35.nq.gz
│   ├── 3c22ad6f209b6027283f28cbc7e55665895bc3f0.nq.gz
│   ├── 3c7c253460dc38803ca963fc2deeaafd89bacf7d.nq.gz
│   ├── 4964d1779e3f2f4f7000e248805bbc45717409e1.nq.gz
│   ├── 5188733ff6d219665bfd9c960b6d066b5ecb5ee8.nq.gz
│   ├── 52fbe412934be663e1dbab6adf7d3ee0f2c02ee3.nq.gz
│   ├── 5d0947454609bdf6c79d9d6523443e79c85448ab.nq.gz
│   ├── 662562438d5713a94b34ee22773be5b041f91de4.nq.gz
│   ├── 6d653b60e6ec272bd04c6e1af4f629786e6a7e8b.nq.gz
│   ├── 720908391ec286c6d86bb8c8eb0e2a93995da67e.nq.gz
│   ├── 731bbf1390329beedc155c484838c15c51376132.nq.gz
│   ├── 7ee3afbac8574e2733a5ea8896daf71bc67ec357.nq.gz
│   ├── 887a2c18f01df0784f690be728f22c1f9d1fa5c4.nq.gz
│   ├── aa2097346b444a1e104d6efd4e7bc72d093fcc39.nq.gz
│   ├── af080d171ba27eb40539dc4859b1712aee331ba0.nq.gz
│   ├── b125b2afb83ec078fe566c61f4e43b44bfaf2dae.nq.gz
│   ├── d32bf4562ee68f78758fad0479547c30571900b3.nq.gz
│   ├── d4860b469e327bfd93a2588446e512e93cd612c2.nq.gz
│   ├── d60b9352e27cd04413a17114fb3100e3e5c55629.nq.gz
│   ├── d9a5b22855c7119adf1ffa3d4f8719ba697c01ac.nq.gz
│   ├── ee308e922188bbf6662d955a61672d6b998893a2.nq.gz
│   ├── f7309b6cdd50b6cb8fd6579671d31b1ff638d388.nq.gz
│   ├── f743d59c04949d1477bf0a4617aa00779e281d81.nq.gz
│   ├── fb461eafa8c16419ed70f483b3d26f58ece6494f.nq.gz
│   └── fd385feb6dee29b7aa26c69e639349b06003736f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 834b0bf8af344c8850d408874214955550474b40.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 41 files
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

[scverse/gatac-reproducibility](https://github.com/scverse/gatac-reproducibility)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
