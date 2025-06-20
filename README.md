# CCLE-metabolic-features

Welcome to the `CCLE-metabolic-features` wiki!

---

## 🧠 Computational Approach

We use a generic metabolic network graph. The network can be any standard metabolic network, but we reconstructed our own compact network **ENGRO2** (Di Filippo et al., 2022), consisting of ~500 reactions.  
We also run the pipeline for the **genome-wide Recon3D** network (~11,000 reactions).

Flux boundaries (i.e., differential constraints) are applied based on gene expression and nutrient data specific to each cell line (Di Filippo et al., 2022).

We then sample the feasible solution space using either:
- **CHRR**
- **CBS** (Galuzzi et al., 2024)

This repository includes both raw samples and summary statistics.

Beyond summary statistics, we compute the **sensitivity** of each reaction, defined as the correlation between its flux and biomass production. This serves as a proxy to predict essentiality.

Alternatively, we can simulate gene knockouts by optimizing for biomass and evaluating the **KO (knockout) effect**. These results are also provided as features.

---

## 🧷 Node Labels

> ⚠️ Labels are available only for a subset of the cell lines for which we generated features.

- **Gene expression data** come from the [CCLE portal](https://sites.broadinstitute.org/ccle/).
- **Essentiality labels** come from the [DepMap portal](https://depmap.org/portal/), including:
  - **CERES normalized scores**
  - **GECKO scores** (available for a smaller subset)

For generating reaction labels:
- **CERES**: gene-level scores are converted to reaction-level:
  - `min()` for AND relationships
  - `max()` for OR relationships

---

## 📁 Data Folder Structure

This repository contains data for different metabolic graphs and their associated features, labels, and stoichiometric matrices.

### 🔹 `ENGRO2` Graph

- **Stoichiometric matrix file**  
  *(Extracted using COBRApy functions)*

- **Feature folder**
  - All sampled fluxes (CHRR)
  - All sampled fluxes (CBS)
  - Sampled statistics (mean, median, mode) – CBS
  - Sampled statistics (mean, median, mode) – CHRR
  - Sensitivity analysis – CBS
  - Sensitivity analysis – CHRR
  - Knockout (KO) simulation results

- **Label folder**
  - CERES normalized scores
  - GECKO normalized scores

### 🔹 `RECON 3D` Graph (genome-wide)  
_Coming soon_

- **Stoichiometric matrix file**  
  *(Extracted using COBRApy functions)*

- **Feature folder**
  - All sampled fluxes (CHRR)
  - All sampled fluxes (CBS)
  - Sampled statistics (mean, median, mode) – CBS
  - Sampled statistics (mean, median, mode) – CHRR
  - Sensitivity analysis – CBS
  - Sensitivity analysis – CHRR
  - KO simulation results

- **Label folder**
  - CERES normalized scores
  - GECKO normalized scores

---

## 📚 References

- Di Filippo, Marzia, et al. "INTEGRATE: Model-based multi-omics data integration to characterize multi-level metabolic regulation." PLoS computational biology 18.2 (2022): e1009337.
- Galuzzi, B. G. et al. (2024). Adjusting for false discoveries in constraint-based differential metabolic flux analysis. Journal of Biomedical Informatics, 150, 104597.
