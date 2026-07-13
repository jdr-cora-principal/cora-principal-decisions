# CORA principal decisions

This public repository records independently reviewed human-principal decisions
for CORA governance gates. It has two separate append-only namespaces:

- `decisions/` contains control-plane decisions conforming to
  `cora.github_principal_decision.v1`.
- `execution-decisions/` contains one-run execution selections conforming to
  `cora.github_principal_execution_decision.v1`.

The normative schemas are under `schemas/`. Prose and examples are informative;
the committed schema bytes are authoritative.

## Authority

The project principal is GitHub account `jdr-cora-principal`, numeric user ID
`302294632`. A record becomes authoritative only when all of these conditions
hold:

1. `jeffrinehart` proposes the exact canonical record through a pull request.
2. `jdr-cora-principal` approves the exact final pull-request head.
3. The principal merges that pull request into protected default branch `main`.
4. An independent verifier confirms the repository, ruleset, CODEOWNERS,
   review, merge, immutable record bytes, ancestry, and complete append-only
   history.

Principal authentication uses GitHub account security. This repository never
stores passwords, private keys, TOTP secrets, recovery codes, or workflow
tokens.

## Rules

- Records are canonical JSON: UTF-8, keys sorted recursively, two-space
  indentation, and one trailing newline.
- Every record is added in its own pull request. Existing record files are
  never edited, renamed, or deleted.
- A successor is a new record that names exactly one predecessor and binds the
  predecessor's record digest and merge commit.
- A denied execution decision is terminal. No granted or denied successor may
  name it as a predecessor or supersede it; any later proposal must use a new
  authorization ID and a separately reviewed execution history.
- Control-plane and execution histories are enumerated separately.
- Missing, denied, expired, stale, superseded, forked, ambiguous, truncated,
  or unverifiable history never grants authority.
- CORA-RAT and EAT may prepare or verify records but cannot act as the project
  principal.
- A principal execution record does not replace the independently required EAT
  conditional decision. Both are required for a protected execution.
- A principal execution record selects the reviewed content-addressed runner
  image and an exact offline JIT runner ID/name/nonce-derived label. It cannot
  bind self-reported per-run boot evidence, because boot occurs only after the
  principal record is merged and independently verified.
- The JIT configuration, short-lived capability key, and narrowly scoped API
  credential are never committed. The owner mounts them into the selected
  disposable runner only after the principal grant is current.

No record in this repository accepts a payload, clears an EAT hold, promotes a
semantic object, authorizes model use, or accepts a scientific claim unless a
future schema and independently reviewed gate explicitly say otherwise.
