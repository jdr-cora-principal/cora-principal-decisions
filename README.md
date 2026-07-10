# cora-principal-decisions
test change
  This repository records human principal decisions for CORA
  governance gates.

  Decision records bind:

  - the principal identity;
  - an exact gate identifier;
  - a granted or denied outcome;
  - the SHA-256 digest of the reviewed evidence;
  - any preceding decision that is superseded.

  ## Authority

  The GitHub account `jdr-cora-principal` is the project principal.

  A decision becomes authoritative only when:

  1. it is added through a pull request;
  2. `jdr-cora-principal` approves the exact pull-request commit;
  3. the pull request is merged into the protected `main` branch.

  Authentication to the principal account is protected by GitHub two-
  factor
  authentication.

  ## Rules

  - Decision records are append-only.
  - Existing decision files must never be edited or deleted.
  - A changed decision requires a new file that names the preceding
  decision.
  - Decision records contain no passwords, private keys, TOTP secrets,
  or
    recovery codes.
  - Approval of a pull request attests to its exact decision content
  and commit.
  - CORA-RAT, SMA-RAT, and EAT may prepare or verify records but
  cannot act as
    the project principal.
  A successor record must set supersedes to the exact decision_id of
  the
  preceding record. Existing records must not be changed or removed.

  Approval applies only to the named gate and exact evidence digest.
