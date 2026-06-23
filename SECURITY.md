# Security Policy

DeWebProtocol works on verifiable data structures, object references, storage
adapters, and cloud-facing services. Security reports may affect proof
verification, serialization, CID and multicodec handling, authentication,
tenant isolation, storage adapters, caching, or synchronization behavior.

## Reporting a Vulnerability

Do not report security vulnerabilities through public GitHub issues,
Discussions, or pull requests.

security contact: vitalikzhou@gmail.com

Until a dedicated security contact is published, please contact the maintainers
through the most appropriate private channel available to you and include
`SECURITY` in the subject or opening line. Maintainers should replace the TODO
above before announcing a public vulnerability-reporting process.

## What to Include

Please include:

- the affected repository and commit, branch, or release;
- a description of the vulnerability and its impact;
- reproduction steps or a proof of concept, if safe to share privately;
- whether the issue affects proof verification, serialization, CID codecs,
  authentication, tenant isolation, storage adapters, caching, or sync behavior;
- any known mitigations or configuration constraints;
- whether you believe the issue is being actively exploited.

## Scope

Security-sensitive areas include:

- proof generation and proof verification;
- MALT root handling and trusted-root assumptions;
- deterministic serialization and canonical encoding;
- CID, multicodec, and path encoding;
- commitment backends and explicit arc handling;
- storage adapters for CAS, object storage, IPFS, Filecoin, and local stores;
- cloud authentication, project isolation, namespace isolation, and API keys;
- cache correctness and stale data handling;
- local daemon, filesystem sync, and future SDK behavior.

## Audit Status

Some DeWebProtocol repositories are experimental and may not have undergone a
complete independent security audit. Do not assume production hardening, formal
verification, or audit coverage unless a specific repository states that with
evidence.

## Coordinated Disclosure

Maintainers will make a best effort to acknowledge private reports, assess
impact, develop fixes, and publish guidance when appropriate. Public disclosure
timelines should be coordinated with maintainers so users have time to update.
