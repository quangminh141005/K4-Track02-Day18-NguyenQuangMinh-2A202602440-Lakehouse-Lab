# Checkpoint completion — 2026-10-05

Required local work from `docs/CHECKPOINTS.md` is complete. All execution used
`/home/qminh/miniconda3/envs/env_vinai_lab/bin/python` (Python 3.11.16).
The audit found eight executed notebooks, output evidence, explanations, INFO,
reflection and AI disclosure already present. Missing screenshots have now been
created from those saved Jupyter outputs. Validation was rerun successfully.

| Checkpoint | Verified evidence |
|---|---|
| 0 — Environment | Nine smoke checks passed; storage is `_lakehouse/`. |
| 1 — Delta | Two JSON commits; actual `thirty` cast error; merged `tier` with two groups. [Screenshot](screenshots/nb01_delta_log.png) |
| 2 — Optimization | 200 → 55 files; saved notebook speedup 9.7×, pruning 55×; per-file ranges printed. [Screenshot](screenshots/nb02_optimize.png) |
| 3 — Time travel | MERGE processed 100K rows; five versions including RESTORE; zero negative scores. [Screenshot](screenshots/nb03_restore.png) |
| 4 — Medallion | Bronze 200,000 → Silver 190,052; Gold 8 dates × 3 models. Extra assertions verify unique combinations, non-null values, p50 ≤ p95, positive cost and bounded error rates. [Screenshot](screenshots/nb04_gold.png) |
| 5 — Iceberg | Catalog-created day(ts) table; pruning 10×; metadata ratio 303%; renamed field ID 4; specs 1 and 2; 5,500 rows readable. [Screenshot](screenshots/nb05_iceberg_catalog.png) |
| 6 — Maintenance | 200 → 11 files; 90% skip; 16.1 MB reclaimed; three planted orphans removed; checkpoint and pointer present; snapshots 20 → 3; 17 stranded manifest lists swept. [Screenshot](screenshots/nb06_maintenance.png) |
| 7 — Vectors | Amplification 200×; int8 5.8× smaller; recall 0.904; topic fidelity 1.000; zero table hits versus eight stale-index hits; eight CDF deletes. [Screenshot](screenshots/nb07_vectors_multimodal.png) |
| 8 — Agents | Two policy partitions; pinned replay 1,578 steps; five list calls / one catalog read; confirmation and task simulation; four illustrative buckets plus UNCLASSIFIED; erased subject has zero current rows. [Screenshot](screenshots/nb08_agents_provenance.png) |
| 9 — Local submission | Eight notebooks, all code cells executed, no error outputs; eight screenshots; INFO, reflection under 200 words, and AI disclosure present. Smoke, 24 tests and 8/8 script runs pass. |

Timing and measurements above refer to the preserved notebook run, rather than
the later script validation. Screenshots render actual saved outputs; full text
and HTML are retained in `evidence/`. Notebook interpretation cells explain the
results and the NB8 simulation/provenance limitations.

## Validation

```bash
make smoke test run-all \
  PY=/home/qminh/miniconda3/envs/env_vinai_lab/bin/python \
  PYTEST=/home/qminh/miniconda3/envs/env_vinai_lab/bin/pytest
```

Result: smoke 9/9, tests 24/24, lightweight scripts 8/8 (25.1 seconds).
See [validation.txt](evidence/validation.txt). The existing notebook execution
script is `scripts/prepare_submission.py`; run it with this environment's Python
to regenerate notebook outputs and text/HTML evidence.

## Student steps

Review the AI-assisted reflection and explanations, then perform the Git/GitHub
checks and submission in `docs/SUBMISSION.md`: fork/remote checks, commit, push,
PR and submit the repo/PR links plus commit SHA. No Git operations or remote
verification were performed during this audit. Optional bonus was not added.
