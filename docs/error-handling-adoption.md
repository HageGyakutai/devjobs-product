# Error handling adoption — devjobs-product

Audit: 2026-10-13; integration baseline `main` at `bf1d1cd79034ea6342bb974b6a48181d92a66ad3`.
Status: **policy proposal; runtime changes not implemented in this PR**.
This is a scoped audit of the listed files, not a complete error/client inventory.

## Baseline

Public product/portfolio documentation only. README explicitly states that source and full checks remain in the private DevJobs repository. There is no runtime error implementation in this repository and none should be copied here. No AGENTS.md existed.

Observed locations: README.md; docs/architecture.md; docs/quality.md; private DevJobs runtime (read-only reference).

## Adapted mandatory target

[Shared Error Handling Standard 1.0.0](error-handling-standard.md):
**Typed Domain/Application Exceptions + Centralized Exception Translation**.

Describe the typed exception/central translation pattern accurately in product documentation. Runtime adoption, API regression tests and exact-SHA Quality Gate belong to private DevJobs. Publish only safe approved contracts/evidence; never copy private source, tokens, provider responses or personal data.

Documentation/agent-policy coverage is applicable here; runtime compliance is not applicable. This PR must not imply that private DevJobs has completed its error-handling migration.

## Compatibility and privacy

Preserve current statuses, JSON/HTML/CLI contracts, messages/field keys, auth/retry/security headers and OpenAPI where present.
No forced JSON/RFC 9457 conversion. Contract changes require a separate owner-approved task.
No cross-repository runtime dependency. Redact secrets; validate/bound correlation identifiers; never suppress cancellation or cleanup failure.
Unknown HTTP failures must remain safe 500; workers retain explicit terminal/retryable/unknown outcomes.

## Pending work and acceptance

Complete the class/raise-site/client/status/body/header or CLI-exit table first.
Add failure/contract/secrecy regression tests, then minimally adapt the existing architecture.
Add AST-aware transport import checks where meaningful. Preserve every existing test and gate.
Run the actual locked checks and real integrations before exact-SHA acceptance.

Existing check commands / applicable verification:

```bash
# Documentation-only repository: review Markdown links and safe product evidence.
# Runtime checks belong to private DevJobs; no Python acceptance is claimed here.
```

Checks have not run for this docs-only proposal. Docker/live-provider validation remains unverified.
Keep PR Draft; owner approval and applicable local Quality Gate on final SHA are required before merge.
No CI workflow changes.
