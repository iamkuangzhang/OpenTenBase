# Rhino-Bird IVFFlat Reproduction Materials

This directory is the reviewer entry point for the Rhino-Bird IVFFlat adaptive build submission in OpenTenBase.

## Minimal Smoke Reproduction

Run from the OpenTenBase repository root:

```bash
bash contrib/pgvector/bench/rhino/reproduce_smoke.sh
```

The script creates a temporary local database, generates deterministic small vectors, builds an IVFFlat index, verifies that the memory-aware path can fall back from Elkan to Yinyang k-means when appropriate, checks that the IVFFlat index is usable by a query, and validates the diagnostic SQL output. It prints explicit PASS/FAIL lines and does not download datasets.

This smoke test is a minimal functional reproduction. It is not the full SIFT/GloVe/GIST benchmark used for the paper-level evaluation.

## Technical Reports

- `docs/IVFFlat_Adaptive_Build_Technical_Report.pdf`
  - Technical report and reproduction guide for the IVFFlat memory-adaptive build and diagnostics work.

- `docs/IVFFlat_Experiment_Environment_and_Results.pdf`
  - Experiment environment, dataset, and detailed result evidence for the SIFT/GloVe/GIST evaluation.

## Notes

- Production code lives under `contrib/pgvector/src/`, `contrib/pgvector/sql/`, and `contrib/pgvector/test/`.
- This `bench/rhino/` directory only contains reviewer-facing reproduction material and documentation.
