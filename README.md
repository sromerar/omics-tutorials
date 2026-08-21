# omics-tutorials

Reproducible, annotated tutorials in single-cell and multi-omics analysis for learning, reference, and method development.

Each folder contains the reproduction of a bioinformatics tutorial using a Jupyter notebook. I run the analysis myself, add explanations throughout, and save the completed notebook with its outputs.

## Tutorials

| Tool | Domain | Status |
|---|---|---|
| [`atlas/`](atlas) | Multi-omic (scRNA-seq + scATAC-seq) single-cell trajectory inference via Weighted Nearest Neighbor graphs ([paper](https://doi.org/10.64898/2026.05.23.727175), [docs](https://atlas-smilies.readthedocs.io/en/latest/)) | ✅ Complete |

More entries will be added here as they're worked through.

## Structure

Each tutorial folder follows the same layout:

```
<tool>/
├── README.md           # overview, what's reproduced, key results
├── notebooks/          # my executed recreation(s), committed with outputs
├── reference/          # unmodified official tutorial notebook(s), for comparison / full-scale reproduction
├── figures/            # exported plots from the executed notebook(s)
├── environment.yml     # conda environment
└── requirements.txt    # pip requirements
```
