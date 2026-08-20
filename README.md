# ATLAS

Annotated reproduction of the ATLAS tutorials for multimodal single-cell trajectory inference.

**Tool:** [ATLAS](https://atlas-smilies.readthedocs.io/en/latest/) (`atlas-smilies`) — a [scverse](https://scverse.org/)-compatible framework for multi-omic trajectory inference from paired single-cell RNA + ATAC data, fusing both modalities via a Weighted Nearest Neighbor (WNN) graph before running pseudotime/fate inference (Palantir or CellRank).

**Paper:** Leclercq, A., Martini, L., Bardini, R., Savino, A., & Di Carlo, S. (2026). *ATLAS: A scverse-compatible package for multi-omic single-cell trajectory inference integration.* bioRxiv. [10.64898/2026.05.23.727175](https://doi.org/10.64898/2026.05.23.727175)

## What's here

| Path | What it is |
|---|---|
| [`notebooks/01_atlas_getting_started.ipynb`](notebooks/01_atlas_getting_started.ipynb) | My own recreation of Tutorials 1 & 2, **executed and committed with real outputs**, run on a small synthetic branching dataset I generate in the notebook. Same ATLAS API calls as the official tutorials (`atlas.pp.preprocessing`, `atlas.tl.PalantirExtension`, WNN + UMAP + Palantir pseudotime). |
| [`reference/`](reference) | The official tutorial notebooks from the [`atlas-smilies`](https://github.com/smilies-polito/atlas-smilies) repo, kept as-is for comparison and for reproducing the full-scale analysis with real data. |
| [`figures/`](figures) | PNG exports of the key plots from the demo notebook. |
| `environment.yml` / `requirements.txt` | Dependencies to reproduce this notebook. |

## Why a synthetic demo?

The official tutorials use real datasets that are large and hosted externally (a ~GB 10x Genomics multiome mouse-brain dataset with an ATAC fragment file for Tutorial 1, and a SHARE-seq hair-follicle dataset for Tutorial 2 — see `reference/README.md` for exact sources). Rather than committing gigabytes of external data to a portfolio repo, `notebooks/01_atlas_getting_started.ipynb` simulates a small branching trajectory (a progenitor population splitting into two lineages) with matched RNA + "gene activity" modalities, and runs it through the **real, unmodified ATLAS API**. The point isn't the biology of the toy data — it's that the notebook proves the pipeline runs correctly end-to-end, with sensible output (pseudotime increases from the progenitor population outward along both simulated lineages, recovered purely from the graph, with no labels given to the algorithm).

To reproduce the full-scale, real-data version of the tutorials, see [`reference/README.md`](reference/README.md).

## Key result

![UMAP colored by simulated cell type](figures/umap_celltype.png)
![UMAP colored by Palantir pseudotime](figures/umap_pseudotime.png)

Pseudotime increases outward from the progenitor cluster along both lineages — recovered entirely from the WNN graph + diffusion pseudotime, with no ground-truth timing given to the algorithm.

## Reproducing the demo notebook

\`\`\`bash
conda env create -f environment.yml
conda activate atlas-tutorial
jupyter notebook notebooks/01_atlas_getting_started.ipynb
\`\`\`

Or with pip:

\`\`\`bash
pip install -r requirements.txt
jupyter notebook notebooks/01_atlas_getting_started.ipynb
\`\`\`

## What I learned working through this

- How ATLAS represents paired multi-omic data as a `MuData` object with `rna` + `activity` (or `atac`) modalities.
- How the WNN graph is constructed to jointly weight transcriptomic and chromatin-accessibility neighborhoods per cell.
- How to plug ATLAS's WNN output into Palantir for pseudotime and fate-probability estimation.
- A real compatibility snag (`atlas.pl.plot_embedding` → `scvelo.pl.scatter` breaking on the installed `pandas` version) and how I worked around it — documented directly in the notebook rather than hidden.
