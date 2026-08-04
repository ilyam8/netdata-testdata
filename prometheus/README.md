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

Consumers must pin an exact `netdata/testdata` commit and verify the manifest
digests before using these files as profile proof. CI must not validate against
the mutable default branch implicitly.
