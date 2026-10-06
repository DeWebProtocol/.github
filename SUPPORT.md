# Support

DeWebProtocol support happens through the relevant GitHub repositories. Please
avoid personal direct-message support requests so issues remain visible,
searchable, and actionable for the project.

## Where to Ask

- Authentication semantics, Root/CID rules, typed queries, proofs, candidates
  and batches, verification, or the Go Object SDK:
  [`malt-core`](https://github.com/DeWebProtocol/malt-core)
- JavaScript/TypeScript APIs, browser Workers, verifier/writer WASM assets,
  package installation, and bundler integration:
  [`malt-ts`](https://github.com/DeWebProtocol/malt-ts)
- Local runtime, CLI/daemon, trusted Roots, public Node API, UnixFS and
  encrypted backup, Merkle DAG import, synchronization, and payload verification:
  [`malt`](https://github.com/DeWebProtocol/malt)
- Experiment runners, comparison adapters, plans, raw-artifact analysis,
  reproducibility, and result provenance:
  [`malt-evaluation`](https://github.com/DeWebProtocol/malt-evaluation)
  (private; access required)
- Public explanations, tutorials, website, and public verification tools:
  [`malt-web`](https://github.com/DeWebProtocol/malt-web)
- Managed gateway service behavior, tenants, identity, authorization, backend
  orchestration, Bucket ACL/commit/ref behavior, S3/Filecoin/IPFS integration,
  managed Console, deployment, and product end-to-end tests:
  [`gateway`](https://github.com/DeWebProtocol/gateway) (private; access required)
- Organization profile, community files, and repository routing:
  [`.github`](https://github.com/DeWebProtocol/.github)

For a question that spans repositories, start with the public
[integration boundaries](https://github.com/DeWebProtocol/malt-core/blob/main/ARCHITECTURE.md#packages-and-integration-boundaries)
and [Node API](https://github.com/DeWebProtocol/malt/blob/main/docs/node-api.md).
If you do not have access to the owning repository, open a non-confidential
routing question in [`.github`](https://github.com/DeWebProtocol/.github/issues).

## Bugs

Open a GitHub issue in the affected repository. Include the command, API call,
commit or branch, expected behavior, actual behavior, logs, and a minimal
reproduction when possible.

For browser problems, also include the SDK version and the verifier/writer
asset provenance. A newer Core release does not change an already packaged
browser artifact. Distinguish installed dependencies from source locks, and
deployed service versions from repository revisions.

## Design Questions

Use GitHub Discussions when they are enabled in the relevant repository. If
Discussions are not enabled, open an issue labeled or titled as a design
question.

## Security Issues

Do not open public issues for security vulnerabilities. Follow
[SECURITY.md](SECURITY.md).

## Response Expectations

DeWebProtocol is an open-source project. Maintainers will respond as capacity
allows, but no individual support channel, service-level agreement, or private
consulting commitment is implied by this repository.
