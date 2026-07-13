# Contributing to DeWebProtocol

Thanks for considering a contribution. DeWebProtocol is building infrastructure
for user-owned, verifiable, storage-independent data. Contributions should keep
that focus clear and should distinguish implemented behavior from future plans.

## Choosing a Repository

- Use [`dewebprotocol/malt`](https://github.com/DeWebProtocol/malt) for protocol
  semantics, MALT objects, explicit arcs, structure commitments, path encoding,
  CIDs, multicodecs, commitment backends, CAS interfaces, proofs, verification,
  benchmarks, evaluation workloads, and reproducibility artifacts.
- Use [`dewebprotocol/malt-web`](https://github.com/DeWebProtocol/malt-web) for
  the public website and documentation site.
- Managed gateway service behavior, tenants, identity, authorization, root
  publication, backend orchestration, cache policy, S3/Filecoin/IPFS
  integration, and product-level end-to-end tests belong to the private
  `gateway` service. Its current integration pins MALT v0.0.5 and owns the
  operation-specific resolve/read/content product integration. Start with MALT's public
  [repository boundary](https://github.com/DeWebProtocol/malt#repository-boundary);
  contributors without private access can open a scoped design issue in
  `dewebprotocol/malt` for routing.
- Planned filesystem client and SDK work may later move into `malt-cli` or
  `malt-ts`. Until those repositories exist, discuss cross-cutting design work
  in the most relevant existing repository.

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

## Testing

Run the target repository's documented test commands before asking for review.
If you cannot run a relevant test, say why in the pull request. For performance
or benchmark changes, include the exact command, environment, and comparison
baseline.

## Code Style and Commits

Follow the conventions of the repository you are changing. DeWebProtocol does
not currently impose a separate organization-wide commit format or governance
process beyond the repository-specific rules.
