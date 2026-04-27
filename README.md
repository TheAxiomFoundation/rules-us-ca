# rules-us-ca

California RuleSpec source registry and policy metadata.

## Contents

- `sources/slices/cdss/calfresh/current-effective/`: CalFresh source slices and sidecar metadata.
- `ftb/<year>/parameters.yaml`: Franchise Tax Board parameter tables retained as structured reference data.
- `tests/integration/`: historical integration fixtures pending RuleSpec migration.
- `.github/workflows/ci.yml`: repository guard for legacy executable formula payloads.

## Conventions

Use RuleSpec YAML for new encoded rules. Keep source text in `sources/slices/` with matching `.meta.yaml` files that record provenance and relations. Large XML or source payloads belong in object storage, with only registry or manifest metadata in Git.

Federal materials belong in `rules-us`. California-administered materials belong here.
