  ### decisions/README.md

  # Principal Decision Records

  This directory contains append-only CORA principal decision records.

  ## Filename

  Use:

  ```text
  YYYY-MM-DD-<gate-id>-<decision-id>.json

  Example:

  2026-07-10-cora-sma-control-plane0-initial.json

  ## Record Format

  {
    "schema": "cora.principal_decision.v1",
    "decision_id": "2026-07-10-control-plane0-initial",
    "principal": {
      "github_login": "jdr-cora-principal"
    },
    "gate_id": "CORA-SMA-CONTROL-PLANE0",
    "decision": "granted",
    "evidence": {
      "subject": "cora_sma_control_plane_review_bundle_v1",
      "sha256": "REPLACE_WITH_64_CHARACTER_LOWERCASE_SHA256"
    },
    "supersedes": null,
    "non_claims": []
  }

  Allowed decisions are:

  granted
  denied
