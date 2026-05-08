# Repolex Knowledge Graph of known-facts/known-types

RDF knowledge graph data for [known-facts/known-types](https://github.com/known-facts/known-types), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download known-facts/known-types
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a495032e08f8d3589156c2df22d8cead6ad81216
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── a495032e08f8d3589156c2df22d8cead6ad81216.nq.gz
│   └── repolex
│       └── a495032e08f8d3589156c2df22d8cead6ad81216
│           └── chunk-001.nq.gz
├── blob
│   ├── 056e19d9380a7f21f48e41ea774f276ebfb7471a.nq.gz
│   ├── 0c7e355102099d71016a3c8648c4d81966bb7274.nq.gz
│   ├── 1130c6579d89336ae07c20152bb03bec4ddaacac.nq.gz
│   ├── 13edb27f8341a15f7ef6805243c5be8572913129.nq.gz
│   ├── 2601b3f4151f2ad62821425751ff1867283aa420.nq.gz
│   ├── 280fb8d04170d32ee9c5f1537fb204382a2602ff.nq.gz
│   ├── 28382cee3616d3a11c77fc1b192c5d18973ce016.nq.gz
│   ├── 3418515ee7d33a07923367f127e00b8a7bdfa777.nq.gz
│   ├── 6c214ae8cb5f30ebe2580b07ee304bd252e734d3.nq.gz
│   ├── 6e8bf73aa550d4c57f6f35830f1bcdc7a4a62f38.nq.gz
│   ├── 747c76aadc0e4250e9bf9fc021e59c09757d49a1.nq.gz
│   ├── 75e3b65f99b29f48ab230e3eab3de8d0b7a9229f.nq.gz
│   ├── a718674ce58c2cb835775828c8a323d259c0848c.nq.gz
│   ├── c7504b17b600cacd0a72d17b05bb8dae214c4791.nq.gz
│   ├── d2d774d685a805fac62723c16262a6ba9ded7549.nq.gz
│   ├── e3e57a8ce4ccbf74759a6df8fa4a3980ff1c9209.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e94d007030c7f349ab7a49bf213a046e494b7efe.nq.gz
│   ├── efb98088164f5786b17e83ed384971fc3c74f93c.nq.gz
│   ├── f5904cc204378e7027a7bf5402e8350a10c50882.nq.gz
│   └── f82ee3557086724919c5226d4af53b519ac391a0.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── a495032e08f8d3589156c2df22d8cead6ad81216.nq.gz
├── filetree
│   └── a495032e08f8d3589156c2df22d8cead6ad81216.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

14 directories, 30 files
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

## Source repository

[known-facts/known-types](https://github.com/known-facts/known-types)

---
*Parsed on 2026-05-08 by [repolex](https://repolex.ai)*
