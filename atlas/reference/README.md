# Official ATLAS tutorial notebooks

These are unmodified copies of the official tutorials from [`smilies-polito/atlas-smilies`](https://github.com/smilies-polito/atlas-smilies) (`docs/notebooks/`), kept here for reference and full-scale reproduction.

| Notebook | Covers | Data required |
|---|---|---|
| `tutorial1_official_getting_started.ipynb` | Building a `MuData` multimodal container, gene-activity computation from scATAC-seq, QC, and the WNN graph | 10x Genomics `e18_mouse_brain_fresh_5k` multiome dataset (RNA+ATAC matrices + ATAC fragments file) + cell-type annotations from [MultiVelo](https://github.com/welch-lab/MultiVelo). Download cells are included at the top of the notebook. |
| `tutorial2_official_palantir.ipynb` | Trajectory inference with Palantir on top of the ATLAS WNN graph | A pre-built `hair.h5mu` (SHARE-seq mouse hair-follicle multi-omic dataset, gene activity already computed) |
| `tutorial3_official_cellrank.ipynb` | Trajectory inference with the CellRank pseudotime kernel | Same as Tutorial 2 |

## Running these for real

1. `pip install atlas-smilies pysam`
2. Run the download cell at the top of `tutorial1_official_getting_started.ipynb` — it fetches the 10x multiome dataset and cell annotations directly.
3. For Tutorials 2 & 3, obtain `hair.h5mu` (see the ATLAS paper/docs for the current hosting location — it wasn't bundled in-notebook) and place it under `data/`.

These downloads were **not** run in this repo's synthetic demo notebook (`../notebooks/`) since the underlying network environment I used to build this repo doesn't have access to `cf.10xgenomics.com`. If you have unrestricted internet access, running these notebooks as-is is the most faithful reproduction of the paper's actual analysis.
