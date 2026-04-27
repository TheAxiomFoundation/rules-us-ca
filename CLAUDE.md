# rules-us-ca Agent Notes

This repo stores California RuleSpec source registry materials and related policy metadata.

## Do

- Keep California-administered source slices under `sources/slices/`.
- Add or update sidecar `.meta.yaml` files with source provenance, relations, and jurisdiction metadata.
- Keep parameter tables as structured YAML when they are useful reference data.
- Keep large source payloads outside Git and point to them through metadata or manifests.

## Do Not

- Reintroduce legacy executable formula payloads.
- Put federal source slices or federal RuleSpec outputs here; use `rules-us`.
- Add generated source payloads to Git.
