# Publication and redaction policy

This repository is the **sanitized public edition** of internal documentation. Its purpose is to share architecture decisions and verifiable results without exposing operational material, personal data, or unnecessary internal details.

## 1. Publication principles

- **Minimal necessary detail.** Show only what is needed to understand decisions and status.
- **Evidence without leakage.** Result summaries may be shown; raw logs and artifact checksums may not.
- **Context before claims.** Every number or status must include its interpretation boundary.
- **Explicit redaction.** Information intentionally withheld is marked `[Redacted 0xnhsec]`.
- **No payloads.** Documentation must not contain exploit examples, credentials, or directly usable offensive commands.

## 2. Exposure matrix

| Area | Public | Redacted / withheld |
|---|---|---|
| Purpose and architecture | Yes | Internal implementation details |
| Module names and domains | Yes | Local paths and build identity |
| Licenses | Yes | Package locations and artifact checksums |
| Reference counts | Yes | Reference contents and payloads |
| Test results | Summary | Raw logs and internal commands |
| Scanner | Risk class and review status | Finding details and example findings |
| Installation | Status and gates | Configuration and profile paths |
| Runtime | Discovery and view flow | Runtime configuration and host identifiers |
| `red-ctf` | Separate package status | Artifact name, package contents, checksum |
| Roadmap | Yes | Internal target dates and engagement details |

## 3. Redaction token

The string `[Redacted 0xnhsec]` means:

- the information exists in internal evidence but is not published;
- the information is not needed to understand the public decision;
- the information must not be reconstructed from this document;
- removing the token does not automatically make the information publishable.

This token is not a TODO and not a sign that the document is unfinished. The document is complete at the chosen exposure level.

## 4. Withheld categories

### 4.1 Identity and environment

- Absolute paths and home-directory names.
- Hostnames, profile names, and machine identifiers.
- Full build identity and runtime configuration.
- Credentials, tokens, and authentication material.

### 4.2 Raw evidence

- Raw test and installation logs.
- Per-finding scanner output.
- Internal artifact checksums.
- Evidence files that could reconstruct the environment.

### 4.3 Operational material

- Payloads, exploits, and offensive command examples.
- Target configuration and engagement results.
- Challenge details or flags.
- Distribution packages and unsanitized reference contents.

## 5. What may be published

- Architecture summary and domain breakdown.
- Module names, licenses, and adoption status.
- Reference counts and domain coverage.
- Test result summaries without raw logs.
- Trust-tier status and the reason for license separation.
- Workflow, gates, and rollback.
- Roadmap with exit criteria.

## 6. Pre-publication checklist

- [ ] No absolute paths or hostnames.
- [ ] No credentials, tokens, or personal identifiers.
- [ ] No payloads or directly usable offensive commands.
- [ ] No raw logs or scanner finding details.
- [ ] No internal checksums or package artifacts.
- [ ] Every claim has an interpretation boundary.
- [ ] `[Redacted 0xnhsec]` is used only for genuinely withheld information.
- [ ] Licenses and the MIT/GPL separation are explained correctly.
- [ ] The document does not claim the entire roadmap is complete.
- [ ] Internal links and Mermaid diagrams are valid.

## 7. Change review

Every public documentation change must pass this review:

1. **Accuracy.** Does the status match internal evidence?
2. **Redaction.** Is any data that should be withheld exposed?
3. **Consistency.** Do numbers and terminology match the other documents?
4. **Claim boundaries.** Could a reader misunderstand the capability?
5. **License.** Is MIT/GPL separation preserved?

If any check fails, the change is not published.

## 8. License and distribution

This documentation follows the repository `LICENSE`. The modules discussed retain their original licenses. Publishing documentation does not grant any additional license to packages, payloads, or skill source that are not included.

## 9. Contact and corrections

Factual corrections can be submitted through a repository issue. Do not request or resend information already marked `[Redacted 0xnhsec]` through public issues.
