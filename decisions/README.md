# Control-plane principal decisions

This namespace contains append-only records governed by
`../schemas/cora-github-principal-decision-v1.schema.json`.

The schema identifier is exactly:

```text
cora.github_principal_decision.v1
```

The top-level fields are exactly:

```text
schema
decision_id
principal
scope
issued_status
evidence_subject
evidence_digest
created_at
supersedes
predecessor
```

Records use `decisions/<decision_id>.json`, are added one per pull request, and
are canonical JSON: UTF-8, recursively sorted keys, two-space indentation, and
one trailing newline. Existing record bytes are immutable.

This schema is retained for the existing CORA/SymMatAlg control-plane review
bundle. It must not be used to select a GitHub Actions execution. Execution
selection uses the separate `execution-decisions/` namespace and schema.
