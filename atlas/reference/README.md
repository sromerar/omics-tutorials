# ATLAS tutorial notebooks

These are unmodified copies of the official tutorials from [`smilies-polito/atlas-smilies`](https://github.com/smilies-polito/atlas-smilies) (`docs/notebooks/`), kept here for reference and full-scale reproduction.

| Notebook | Covers | Data required |
|---|---|---|
| `tutorial1_official_getting_started.ipynb` | Building a `MuData` multimodal container, gene-activity computation from scATAC-seq, QC, and the WNN graph | 10x Genomics `e18_mouse_brain_fresh_5k` multiome dataset (RNA+ATAC matrices + ATAC fragments file) + cell-type annotations from [MultiVelo](https://github.com/welch-lab/MultiVelo). Download cells are included at the top of the notebook. |
| `tutorial2_official_palantir.ipynb` | Trajectory inference with Palantir on top of the ATLAS WNN graph | A pre-built `hair.h5mu` (SHARE-seq mouse hair-follicle multi-omic dataset, gene activity already computed) |
| `tutorial3_official_cellrank.ipynb` | Trajectory inference with the CellRank pseudotime kernel | Same as Tutorial 2 |
