# Security Policy

DeWebProtocol works on verifiable data structures, object references, storage
adapters, and cloud-facing services. Security reports may affect proof
verification, serialization, CID and multicodec handling, authentication,
browser SDK assets and Workers, sessions, Passkey/WebAuthn ceremonies,
tenant/Bucket isolation, candidate materialization, quota accounting,
initialization or migration, storage adapters, caching, or synchronization.

## Reporting a Vulnerability

Do not report security vulnerabilities through public GitHub issues,
Discussions, or pull requests.

Current security contact: [security@deweb.world](mailto:security@deweb.world)

Please contact the maintainers privately and include `SECURITY` in the subject
or opening line. If a repository enables GitHub private vulnerability reporting,
that repository-specific reporting channel can also be used.

## What to Include

Please include:

- the affected repository and commit, branch, or release;
- a description of the vulnerability and its impact;
- reproduction steps or a proof of concept, if safe to share privately;
- whether the issue affects proof verification, serialization, CID codecs,
  authentication, browser SDK assets or sessions, Passkey/WebAuthn,
  tenant/Bucket isolation, candidate/batch materialization, quota, storage
  adapters, caching, or synchronization;
- for browser reports, the SDK version and verifier/writer asset provenance;
- any known mitigations or configuration constraints;
- whether you believe the issue is being actively exploited.

## Scope

Security-sensitive areas include:

- proof generation and verification against the exact Root, traversal, and query;
- accepted/candidate Root separation, observed heads, and explicit trust promotion;
- complete candidate validation, retained state, ordered batches, retry identity,
  and materialization-receipt binding;
- Object graph commits, local deltas, and application payload binding;
- deterministic serialization, label and coordinate encodings, CIDs,
  multicodecs, and commitment backends;
- browser Worker lifecycle, Core release locks, WASM provenance, and asset integrity;
- storage adapters, CID-bound payload reads, and data isolation;
- cloud authentication, account provisioning, password handling,
  Passkey/WebAuthn ceremonies, session cookies, origin/CSRF enforcement, and
  administrator authorization;
- tenant/Bucket ACL isolation, ref compare-and-swap, conflict-branch
  preservation, and API keys;
- public Node API authorization and lifecycle checks across in-process services
  and HTTP adapters;
- tier enforcement, quota reservation/commit/reconciliation, and cross-tenant
  accounting isolation;
- explicit service initialization, configuration and secret-file handling,
  legacy-state adoption, migration, and rollback;
- snapshot/cache identity, stale data handling, and shared or public-CID access;
- local daemon IPC, encrypted UnixFS and key handling, staged writes,
  stash-before-pull recovery, filesystem synchronization, and mount behavior.

Authentication evidence establishes integrity relative to a selected Root.
Access control and local Root acceptance are separate policies. Candidate
deltas and materialization receipts are not portable state-transition proofs,
and permission changes cannot recall bytes already held by a client.

## Audit Status

Some DeWebProtocol repositories are experimental and may not have undergone a
complete independent security audit. Do not assume production hardening, formal
verification, or audit coverage unless a specific repository states that with
evidence.

## Coordinated Disclosure

Maintainers will make a best effort to acknowledge private reports, assess
impact, develop fixes, and publish guidance when appropriate. Public disclosure
timelines should be coordinated with maintainers so users have time to update.
