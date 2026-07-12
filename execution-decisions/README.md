# Principal execution decisions

This namespace contains append-only one-run selections governed by
`../schemas/cora-github-principal-execution-decision-v1.schema.json`.

The schema identifier is exactly:

```text
cora.github_principal_execution_decision.v1
```

Each record binds one EAT authorization, frozen CORA commits, one default-branch
workflow and queued run, the canonical dispatch-input digest and nonce, exact
payload/producer/consumer identities, one immutable runner image and observer
envelope, a short validity window, and one-use scope.

Records use `execution-decisions/<decision_id>.json`, are added one per pull
request, and are canonical JSON: UTF-8, recursively sorted keys, two-space
indentation, and one trailing newline. Existing record bytes are immutable.

A `granted` record selects only the exact run named in that record. A `denied`,
expired, stale, superseded, ambiguous, or unverifiable record grants nothing.
The record cannot replace the EAT decision it cites, accept the held payload,
or clear any EAT hold.
