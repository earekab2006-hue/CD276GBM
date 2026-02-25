[README (1).md](https://github.com/user-attachments/files/25552465/README.1.md)
# CD276 (B7-H3) in Glioblastoma: Drug Efflux Transporter Inverse Relationship

Analysis code for:

**"Inverse relationship between CD276 (B7-H3) expression and drug efflux transporter capacity in glioblastoma: implications for antibody-drug conjugate therapy"**

Varshith Kotagiri & Elizabeth Baker

## Overview

This repository contains the complete analysis pipeline reproducing all figures and statistics reported in the manuscript. The analysis demonstrates that CD276-high glioblastoma tumours exhibit reduced expression of drug efflux transporters ABCG2 and ABCB1, identifying a population with both high antibody-drug conjugate (ADC) target expression and enhanced payload retention.

## Reproducing the Analysis

The entire analysis runs as a single Kaggle notebook.

### Setup

1. Create a new Kaggle notebook at [kaggle.com](https://www.kaggle.com/)
2. Add the following datasets (use the "Add data" button):
   - **TCGA PanCancer Atlas GBM**: `cbioportal/gbm_tcga_pan_can_atlas_2018`
   - **TCGA Firehose Legacy GBM**: `cbioportal/gbm_tcga`
   - **TCGA 2013 GBM**: `cbioportal/gbm_tcga_pub2013`
   - **CPTAC GBM**: `cbioportal/gbm_cptac_2021`
   - **GBmap Single-Cell**: `emmanueldiogu/gbmap` (GBMCore h5ad file)
3. Paste the contents of `CD276_Complete.py` into a single code cell
4. Run the cell

### Outputs

The notebook generates 6 figures as 300 DPI PNG files in `/kaggle/working/`:

| File | Description |
|------|-------------|
| `Figure1_Prognostic_Validation.png` | TCGA KM curves, CPTAC protein KM, RNA–protein correlation |
| `Figure2_CD276_vs_PDL1.png` | CD276 vs PD-L1 head-to-head comparison |
| `Figure3_SingleCell.png` | CD276 expression across 20 cell types (338,564 cells) |
| `Figure4_EffluxPump_KeyFinding.png` | Efflux transporter boxplots, volcano plot, CD276/MGMT stratification |
| `SuppFig_ForestPlot.png` | Forest plot across all cohorts and multivariate models |
| `SuppFig_PathwayEnrichment.png` | Gene set enrichment bars and ABC transporter family detail |

All statistical results (Cox regression tables, gene set p-values, concordance indices, etc.) are printed to stdout.

## Data Sources

All data used in this study are publicly available. No new data were generated.

| Dataset | Source | Access |
|---------|--------|--------|
| TCGA GBM (3 pipelines) | [cBioPortal](https://www.cbioportal.org/) | Open access |
| CPTAC GBM | [Proteomic Data Commons](https://pdc.cancer.gov/) | Open access |
| GBmap single-cell | [Ruiz-Moreno et al. 2022](https://doi.org/10.1101/2022.08.27.505439) | Open access |

## Key Findings

- CD276 is an independent prognostic biomarker (multivariate HR=1.34, p=0.038 after adjusting for age, sex, MGMT, IDH1)
- ABCG2 and ABCB1 are significantly downregulated in CD276-high tumours (0.66× and 0.67×, both p≤0.0001)
- Single-cell analysis localises CD276 primarily to tumour vasculature (mural cells, endothelial cells)
- CD276 outperforms PD-L1 across all prognostic metrics
- Combined CD276/MGMT stratification identifies an ultra-high-risk population (Δ=8.6 months, p=0.0015)

## Requirements

See `requirements.txt`. The notebook was developed and tested on Kaggle (Python 3.10, Ubuntu 22.04).

## License

MIT License. See `LICENSE`.
