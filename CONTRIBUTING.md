# Contributing to DeWebProtocol

Thanks for considering a contribution. DeWebProtocol is building infrastructure
for user-owned, verifiable, storage-independent data. Contributions should keep
that focus clear and should distinguish implemented behavior from future plans.

## Choosing a Repository

- Use [`malt-core`](https://github.com/DeWebProtocol/malt-core) for authentication
  semantics, Root/CID rules, coordinate derivation, commitment backends, typed
  queries, verification, candidates and batches, schemas, conformance, the Go
  Object SDK, and implementation-bound MIPs.
- Use [`malt-ts`](https://github.com/DeWebProtocol/malt-ts) for the supported
  JavaScript/TypeScript API, declarations, browser Workers, reproducible WASM
  assets, package distribution, and bundler integration. Core remains normative
  for the authentication semantics those assets execute.
- Use [`malt`](https://github.com/DeWebProtocol/malt) for the local runtime,
  CLI/daemon, accepted/candidate Root policy, public Node API, Gateway transport,
  UnixFS and encrypted backup behavior, synchronization, payload verification,
  and IPFS-compatible Merkle DAG import.
- Use [`malt-evaluation`](https://github.com/DeWebProtocol/malt-evaluation)
  (private; access required) for experiment runners, comparison adapters,
  plans, schemas, raw-artifact analysis, and result provenance. The repository
  root is the only active evaluator module. Product correctness E2E belongs to
  `gateway`; historical results keep their original source and experiment pins.
- Use [`malt-web`](https://github.com/DeWebProtocol/malt-web) for public
  explanations, tutorials, the documentation site, and public verification tools.
- Managed gateway service behavior, tenants, identity, authorization, root
  publication, managed Bucket ACL/commit/ref synchronization, backend
  orchestration, cache policy, S3/Filecoin/IPFS integration, deployment, and
  product-level end-to-end tests belong to the private
  [`gateway`](https://github.com/DeWebProtocol/gateway) service. It implements
  the public Node API and owns the managed Console. Changes to authorization
  must cover both in-process service calls and HTTP adapters.
- Use [`.github`](https://github.com/DeWebProtocol/.github) for the organization
  profile, default community files, and non-confidential repository-routing
  questions, including when a relevant repository requires private access.

Start with the public [integration boundaries](https://github.com/DeWebProtocol/malt-core/blob/main/ARCHITECTURE.md#packages-and-integration-boundaries)
and [Node API](https://github.com/DeWebProtocol/malt/blob/main/docs/node-api.md)
when a change spans repositories. Keep protocol contracts in Core, browser
distribution in `malt-ts`, and service or application policy in its owning
repository. Public explanations should link to these sources of truth.

If you are unsure where a change belongs, open a short design issue before
starting implementation.

## Issues and Discussions

Use issues for concrete bugs, missing documentation, proposed changes, and
implementation tasks. Use GitHub Discussions when enabled for broader design
questions. If Discussions are not enabled in the target repository, use an issue
with a clear title and enough context for maintainers to route it.

Do not report security vulnerabilities in public issues. Follow
[SECURITY.md](SECURITY.md) instead.

## Bug Reports

A useful bug report should include:

- the repository, commit, branch, or release you tested;
- your operating system and toolchain versions;
- the command or API call that failed;
- the expected behavior;
- the actual behavior, including logs or error messages;
- a minimal reproduction when possible;
- whether the issue affects proof verification, serialization, CID handling,
  storage adapters, authentication, tenant isolation, or gateway policy.

## Feature Proposals

A useful feature proposal should explain:

- the user or developer problem being solved;
- the proposed API, protocol behavior, or repository boundary;
- how the design preserves verifiability and storage independence;
- compatibility impact on existing data, APIs, encodings, proofs, or test
  vectors;
- whether a proposed write path affects locally computed candidates, ordered
  batches, materialization receipts, observed heads, publication, or local Root
  acceptance, and how those distinct boundaries remain separate;
- alternatives considered and why they are not sufficient;
- any open research, security, or performance questions.

Avoid proposing product promises that are not supported by the current
repositories.

## Pull Requests

Before opening a pull request:

- keep the change focused on one repository and one topic;
- follow the target repository's local style, tooling, and commit conventions;
- update documentation when behavior or public APIs change;
- add or update tests for changed behavior;
- include benchmark updates when changing benchmarked paths;
- avoid mixing protocol changes with unrelated cleanup;
- explain the verification you ran.

Protocol, encoding, wire-format, proof, or commitment changes should include
tests and, when applicable, cross-language test vectors. Changes that affect
benchmarks or evaluation artifacts should keep reproduction steps clear.
Browser SDK releases must bind an exact published Core release and verify
artifact provenance and checksums. Cross-repository API changes should check
the selected consumer revisions and direct/HTTP capability parity.
Managed-Bucket changes should test concurrent clients, stash-before-pull
recovery, exact candidate/base preservation, ref compare-and-swap, and the rule
that only `status: "branched"` makes HTTP 409 a successful preservation
outcome.

Keep MALT-owned package and repository release versions on `v0.0.x` until
Core publishes `v0.1.0`. Third-party dependency versions are independent.

## Testing

Run the target repository's documented test commands before asking for review.
If you cannot run a relevant test, say why in the pull request. For performance
or benchmark changes, include the exact command, environment, and comparison
baseline.

## Code Style and Commits

Follow the conventions of the repository you are changing. DeWebProtocol does
not currently impose a separate organization-wide commit format or governance
process beyond the repository-specific rules.
