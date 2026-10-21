<p align="center">
  <img src="../../snxx-project.png" alt="SNXX logo" width="140">
</p>

# RTA-SNXX Documentation

<p align="center">
  <strong>English</strong> · <a href="../README.md">Bahasa Indonesia</a>
</p>

This documentation explains how red-team modules from several source repositories were mapped, consolidated, adopted, verified, and published for SNXX.

## Reading order

| Order | Document | Question answered |
|---:|---|---|
| 0 | [Scope and authorization](00-SCOPE.md) | What are the work boundaries and disallowed claims? |
| 1 | [Adoption report](01-ADOPTION-REPORT.md) | What was adopted, what was the result, and what are the claim boundaries? |
| 2 | [Workflow](02-WORKFLOW.md) | What is the work sequence and where are the decision gates? |
| 3 | [Architecture](03-ARCHITECTURE.md) | What are the system layers and trust boundaries? |
| 4 | [Verification](04-VERIFICATION.md) | What evidence supports the current status? |
| 5 | [Publication](05-PUBLICATION.md) | What is published on GitHub and what is redacted? |
| 6 | [Roadmap](06-ROADMAP.md) | What remains open and what are the exit criteria? |

## Diagrams

Raw Mermaid files are available in [`diagrams/`](diagrams/):

- [`01-adoption-workflow.mmd`](diagrams/01-adoption-workflow.mmd) — adoption flow from inventory to publication.
- [`02-verification-workflow.mmd`](diagrams/02-verification-workflow.mmd) — verification and evidence handling flow.
- [`03-runtime-load-flow.mmd`](diagrams/03-runtime-load-flow.mmd) — module loading flow at runtime.

The same diagrams are embedded in the [workflow](02-WORKFLOW.md) and [architecture](03-ARCHITECTURE.md) documents so GitHub can render them directly.

## Redaction convention

The string `[Redacted 0xnhsec]` marks information intentionally withheld from publication. It is not an unfilled placeholder. Category details and rationale are in the [publication policy](05-PUBLICATION.md).

## Document status

- **Version:** 1.0
- **Date:** 21 October 2026
- **Scope:** Phase 1 adoption and its public documentation
- **Nature:** documentation; not code or operational package distribution
