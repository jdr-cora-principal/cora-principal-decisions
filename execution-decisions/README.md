# Principal execution decisions

This namespace contains append-only one-run selections governed by
`../schemas/cora-github-principal-execution-decision-v1.schema.json`.

The schema identifier is exactly:

```text
cora.github_principal_execution_decision.v1
```

Each record binds one EAT authorization, frozen CORA commits, one default-branch
workflow and queued run, the canonical dispatch-input digest and nonce, exact
payload/producer/consumer identities, one reviewed immutable runner image and
observer envelope, a short validity window, and one-use scope. The reviewed
image binding consists of its content-addressed identity plus provenance and
SBOM digests. Per-run boot evidence is deliberately not part of this record.

The owner may create the one-shot JIT configuration and its offline repository
runner record before proposing P. P binds that exact numeric runner ID, the
runner name `eat-distdet-runner-<dispatch_nonce>`, and the label
`eat-distdet-<dispatch_nonce>`. The dispatch input label, runner label, runner
name, run name, and dispatch nonce must all carry the same nonce; the separate
record nonce remains unique. The owner must not mount the JIT configuration,
HMAC key, API credential, or start the container until P is merged and verified.

Authenticated boot and outer-observer evidence can exist only after that start.
They belong in CORA's resulting execution receipt and attestation, where they
must bind the exact selected runner and reviewed image. Adding a per-run boot
digest to P is schema-invalid and must fail closed.

The one-shot capability is transported only as a non-secret repository-level
GitHub Actions variable. Its short-lived HMAC key and narrowly scoped API
credential are owner-mounted into the exact JIT container after P is merged;
they are not stored in this repository or CORA. No GitHub environment or
environment-variable API is part of this contract.

Records use `execution-decisions/<decision_id>.json`, are added one per pull
request, and are canonical JSON: UTF-8, recursively sorted keys, two-space
indentation, and one trailing newline. Existing record bytes are immutable.

A `granted` record selects only the exact run named in that record. A `denied`,
expired, stale, superseded, ambiguous, or unverifiable record grants nothing.
The record cannot replace the EAT decision it cites, accept the held payload,
or clear any EAT hold.

Authority also requires independent live verification of the principal login
and numeric ID, repository ID, protected default-branch head, ruleset,
CODEOWNERS, exact PR head, principal review, merge, record blob, append-only
history, predecessor/supersession continuity, and absence of pagination or API
uncertainty. Those post-merge governance facts are evidence about P; they are
not self-asserted inside P.
