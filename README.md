# Repolex Knowledge Graph of certifi/certifi-prompt

RDF knowledge graph data for [certifi/certifi-prompt](https://github.com/certifi/certifi-prompt), parsed by [repolex](https://repolex.ai).

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
rlex download certifi/certifi-prompt
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── c5ccd2e61647dd2fc91aebaa7a061f7f74e7d03a
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── c5ccd2e61647dd2fc91aebaa7a061f7f74e7d03a
│           └── chunk-001.nq.gz
├── blob
│   ├── 4e3c589b8477af827d948f3aa9ae9d0c6ea1a69f.nq.gz
│   ├── cf599dbc89f617ccc5bcc303b6a7468e7131a332.nq.gz
│   ├── d6466b602473a2683ccf84a9f6c6dce140a058e3.nq.gz
│   └── ddf76e25f3bcf57e58d6f1c101000cd45786432c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── c5ccd2e61647dd2fc91aebaa7a061f7f74e7d03a.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 10 files
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

[certifi/certifi-prompt](https://github.com/certifi/certifi-prompt)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
