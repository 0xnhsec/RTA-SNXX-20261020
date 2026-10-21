# Scope and authorization

This document defines the boundaries of the work reported in this repository. The focus is skill adoption and documentation, not an engagement against external targets.

## 1. Project identity

| Attribute | Value |
|---|---|
| Project name | `RTA-SNXX-20261020` |
| RTA | *Red Team Agent* |
| SNXX | A proper noun; not an acronym |
| 20261020 | Date in `YYMMDD` format: 20 October 2026 |
| Type | Skill adoption, verification, and architecture documentation |
| Subject | Red-team modules and the SNXX skill tree |
| Environment | Local and isolated |
| Report date | 21 October 2026 |
| Classification | Sanitized public edition |

Full project name: **Red Team Agent — SNXX — 20 October 2026**.

## 2. In scope

- Inventory of four source repositories and 128 unique skills.
- Domain consolidation into modules that can be selected opt-in.
- Authoring contracts, reference routing, and license metadata.
- Policy review and trust tiers.
- Opt-in installation in a temporary profile.
- Verification of discovery, `skill_view`, and reference reads.
- Separation of the GPL package from the MIT tree.
- Sanitized public documentation.

## 3. Out of scope

- Testing against a target, host, or network without a written scope.
- Redistribution of skill source, payloads, or operational packages.
- Performance claims or real-target completion claims.
- Publication of raw logs, absolute paths, credentials, or artifact checksums.
- Common/engineering skills outside Phase 1.
- Functional gaps that do not yet have new evidence.

## 4. Network profile

The documented work did not use a network profile to attack a target. All installation checks and module reads were performed in a local or isolated temporary environment. No external host is a target of this report.

## 5. Authorization

Changes allowed in Phase 1:

- add or update modules under `optional-skills/`;
- add contract tests and invariants;
- update documentation, manifests, and evidence;
- create a separate GPL package for `red-ctf`;
- perform test installation in a temporary profile.

Changes not performed:

- modify the SNXX core runtime;
- copy `red-ctf` into the MIT tree;
- activate offensive modules in the default profile;
- publish internal data without redaction;
- push or automatically synchronize to a public repository.

## 6. Publication boundary

This is public documentation. Information not required to understand the decisions and status is replaced with `[Redacted 0xnhsec]`. Withheld categories are described in the [publication policy](05-PUBLICATION.md).

## 7. Claim boundaries

This scope does not permit the following claims:

- all 128 skills have been adopted;
- `red-ctf` can already solve a challenge end-to-end;
- `red-reverse` is complete;
- the entire roadmap is finished;
- this documentation is an operational package distribution.
