# DeWebProtocol

**User-owned data infrastructure for the AI era.**

DeWebProtocol builds infrastructure for Personal Online Datastores: data stores
that users can hold, move, verify, and authorize across applications and storage
providers. In many cloud and AI systems today, user data lives inside
platform-controlled databases and object stores. Users can usually access it
only through platform APIs, and the structure connecting objects can disappear
when a service goes away.

Our long-term goal is an open and verifiable data layer where users own their
data, applications operate on user-controlled objects, and storage providers can
be replaced without losing data integrity or structure.

## MALT

MALT is DeWebProtocol's current core project. It defines an authenticated graph
semantic layer over immutable content-addressed payloads, so object content and
authenticated relationships can be independently stored, resolved, updated, and
verified.

Traditional content-addressed storage and Merkle DAG systems often embed object
references directly inside object content. That works well for immutable
objects, but it couples traversal, proof generation, reference updates, object
rewrites, and data layout to the same object boundary.

MALT keeps payloads as ordinary immutable content-addressed objects and
authenticates the mutable relationships among them using typed list/map roots
and verifier-facing proofs. Technically, MALT encodes list and map relations as
canonical cells and authenticates them with vector-commitment-style backends,
producing compact proofs for the specific path or reference a client queried.
Clients hold a trusted MALT root and verify references and proofs returned by
untrusted gateways, storage services, caches, or materialized indexes.

MALT is not a blockchain and does not depend on one storage provider. It can run
over IPFS, Filecoin, S3, local CAS implementations, or other object and
content-addressed storage backends.

**Status:** MALT is an experimental reference implementation. It is runnable end
to end, but its public APIs, ProofList schemas, wire formats, and deployment
policies may change. It is not production-ready.

## What Works Today

The current [`malt`](https://github.com/DeWebProtocol/malt) repository provides
an end-to-end experimental reference implementation:

- authenticated list and map semantics
- root-relative add, resolve, verify, and writer-mutation workflows
- a local daemon and reference command-line client
- proof-bearing HTTP reads for files, directories, and byte ranges
- immutable payload storage through external CAS backends
- KZG and IPA commitment backends
- overwrite and versioned ArcTable modes
- UnixFS-style application layouts
- reproducible evaluation workloads for traversal, proof overhead, storage
  overhead, and rewrite amplification

## Current Reference Implementation

```mermaid
flowchart TB
  app["Applications / reference CLI / Go client"] --> api["MALT daemon and HTTP API"]
  api --> rw["Resolver / Writer"]
  rw --> semantics["Authenticated list / map semantics"]
  semantics --> proofs["ProofList and commitment backends"]
  semantics --> arctable["ArcTable materialization"]
  rw --> cas["External CAS / IPFS / local CAS"]
```

The current `malt` core repository includes a reference CLI and local daemon.
The planned standalone `malt-cli` repository will evolve this reference surface
into a filesystem-oriented client and synchronization runtime.

## Planned Product Architecture

```mermaid
flowchart TB
  cli["malt-cli"] --> gateway["malt-gateway / MALT Cloud"]
  ts["malt-ts"] --> gateway
  other["other SDKs"] --> gateway
  gateway --> core["malt core"]
  core --> filecoin["Filecoin / IPFS"]
  core --> s3["S3"]
  core --> local["local CAS"]
```

`malt-gateway`, standalone `malt-cli`, and `malt-ts` are planned product
surfaces. They are listed to describe the intended project structure, not to
claim that those repositories are currently usable.

## Repositories

| Repository | Role | Status |
| --- | --- | --- |
| [`malt`](https://github.com/DeWebProtocol/malt) | Core semantics, reference implementation, CLI/daemon reference surface, benchmarks, and evaluation | Experimental reference implementation |
| [`malt-web`](https://github.com/DeWebProtocol/malt-web) | Public website, conceptual documentation, and user-facing design narrative | Active |
| `malt-gateway` | Multi-tenant MALT Cloud backend for storing, resolving, and serving MALT objects | Planned |
| `malt-cli` | Standalone filesystem client, local runtime, and synchronization bridge | Planned |
| `malt-ts` | TypeScript SDK for persistent and verifiable application objects | Planned |

The planned repositories are listed to describe the intended project structure.
They are not linked until public repositories exist.

## Documentation Ownership

The `malt` repository owns implementation-bound specifications, schemas, wire
formats, API behavior, test vectors, evaluation documentation, and MIPs under
`docs/mips`. `malt-web` owns conceptual explanations, tutorials, product
narratives, and user-facing documentation. We do not maintain a separate
`malt-docs` repository today.

## Getting Started

- To understand the protocol, object model, proof semantics, and research
  artifact, start with [`dewebprotocol/malt`](https://github.com/DeWebProtocol/malt).
- To read the public website and documentation source, see
  [`dewebprotocol/malt-web`](https://github.com/DeWebProtocol/malt-web).
- To build a hosted service, follow the planned `malt-gateway` work.
- To synchronize local files, follow the planned `malt-cli` work.
- To define verifiable application objects in TypeScript, follow the planned
  `malt-ts` work.

## Research and Evaluation

MALT is developed as both a systems research project and an experimental
reference implementation. The core repository contains benchmarks, evaluation
workloads, and reproducibility artifacts for studying traversal latency, proof
size, and rewrite amplification in authenticated object graphs.

We avoid claiming production readiness, audit status, deployment scale, or
performance numbers unless they are backed by the current repositories.

## Contributing

Useful contribution areas include commitment backends, storage adapters, IPLD
and CID codecs, SDKs, test vectors, benchmarks, documentation, local-first
synchronization, and security review.

Before opening a pull request, check the target repository's README and local
contribution notes. Protocol, encoding, wire-format, or proof changes should
include tests and, when applicable, cross-language test vectors.

Security issues should not be reported through public issues. See
[SECURITY.md](https://github.com/DeWebProtocol/.github/blob/main/SECURITY.md)
for the current reporting guidance.
