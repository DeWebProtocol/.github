# Security Policy

DeWebProtocol works on verifiable data structures, object references, storage
adapters, and cloud-facing services. Security reports may affect proof
verification, serialization, CID and multicodec handling, authentication,
tenant/Bucket isolation, client-root materialization, storage adapters,
caching, or synchronization behavior.

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
  authentication, tenant/Bucket isolation, client-root materialization, storage
  adapters, caching, or sync behavior;
- any known mitigations or configuration constraints;
- whether you believe the issue is being actively exploited.

## Scope

Security-sensitive areas include:

- proof generation and proof verification;
- MALT root handling and trusted-root assumptions;
- client-root update-view, bundle, exact-candidate, and materialization-receipt
  binding;
- deterministic serialization and canonical encoding;
- CID, multicodec, and path encoding;
- commitment backends and explicit arc handling;
- storage adapters for CAS, object storage, IPFS, Filecoin, and local stores;
- cloud authentication, tenant/Bucket ACL isolation, ref compare-and-swap,
  conflict-branch preservation, and API keys;
- cache correctness and stale data handling;
- local daemon, stash-before-pull recovery, filesystem sync, and future SDK
  behavior.

## Audit Status

Some DeWebProtocol repositories are experimental and may not have undergone a
complete independent security audit. Do not assume production hardening, formal
verification, or audit coverage unless a specific repository states that with
evidence.

## Coordinated Disclosure

Maintainers will make a best effort to acknowledge private reports, assess
impact, develop fixes, and publish guidance when appropriate. Public disclosure
timelines should be coordinated with maintainers so users have time to update.
