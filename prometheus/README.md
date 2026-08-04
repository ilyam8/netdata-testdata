# Prometheus profile evidence

This directory stores the bulky, machine-readable evidence used to validate
stock Prometheus profiles in `netdata/netdata`.

## Data boundary

- `profiles/<profile>/fixtures/` contains sanitized, source-derived synthetic
  Prometheus exposition.
- `profiles/<profile>/SOURCE-INVENTORY.tsv` contains the generated
  source-family-to-profile reconciliation ledger.
- `profiles/<profile>/manifest.yaml` records the size and SHA-256 digest of
  every evidence file.

These fixtures are structural unions assembled from public exporter source and
documentation. Mutually exclusive releases, roles, features, and exporter
modes may coexist to exercise the complete declared profile surface. They are
not recordings of one realizable deployment.

Operational dumps, credentials, private endpoints, and real deployment label
values must not be committed here. The compact operator model, validation job,
validation summary, source revisions, and detailed provenance remain in the
matching `src/go/plugin/go.d/collector/prometheus/profile-proofs/<profile>/`
directory in `netdata/netdata`.

## Consumer contract

Consumers use the latest `netdata/testdata` `master` and verify the referenced
manifest plus every file size and SHA-256 digest it declares. The default branch
is the transport; immutable paths and content digests are the reproducibility
boundary, so consumers do not need a repository commit lock.

## Producer contract

- A merged profile-evidence directory is immutable. Do not modify or delete a
  manifest, source inventory, or fixture referenced by a merged Netdata commit.
- Changed evidence must use a new `profiles/<profile-revision>/` directory with
  a new manifest. The current unversioned profile directories are their initial
  revisions.
- The Prometheus evidence workflow rejects edits or deletions in existing
  profile-revision directories and rejects new files added below an existing
  directory.
- Land the testdata change before the Netdata change that references its new
  manifest.
