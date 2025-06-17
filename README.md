Welcome to the CCLE-metabolic-features wiki!

Computatioanl Approach We use a generic metabolic network graph. The metabolic network can be any standard metabolic network. But we reconstructed our own metabolic network (ENGRO2\cite{di2022integrate}) of about 500 reactions. We run the approach also for the genome-wide metabolic networks Recon3D of about 11000 reactions. We set differential constraints (flux boundaries) according to gene-expression data (and nutrients) of a given cell \cite{di2022integrate}.

We can sample the obtained feasible region. Different sampling techniques can be used. We use CHRR or CBS (\cite{galuzzi2024adjusting}) This repository includes both the samples and summary statistics.

Beyond summary statistics, we also have the correlation of each reaction flux with biomass that could be a good proxy to predict essentiality. We call it sensitivity.

In alternative to sampling, we can also optimize for growth and perform deletion simulations. We provide the simulated deletion effect as feature. We call it KO.

section{Node labels} NNotice that we have labels for only a subset of the cell lines for which we generated the features.

The cell lines gene expression data use to generate the features were taken from \href{https://sites.broadinstitute.org/ccle/}{CCLEA}.

For the labels, we used the DEPMAP database \href{https://depmap.org/portal/}{CCLEA}. The scores can have different normalizations.

We used either the CERES normalized score that exist for many cells and gecko scores that exist for a smaller subset of cells (\cite{meyers2017computational}). We are not really familiar yet with the different normalization, but it involves using also other omics, likely that's why some normalization are not available for all cells.

Given that the labels are associated to the node, we need different labels if we change the graph.

We converted the CERES gene scores into reactions scores by takin the minimum score for genes in AND, the maximum for genes on OR.

Given that scFEA network aggregates reactions into modules, we need a label for the modules. So we took the minimums score among the reactions in the modules. we assume that given that a module is a linear chain of reactions, if almost one is essential than the entire module its essential.

📁 Data Folder Structure
This repository contains data for different metabolic graphs and their associated features, labels, and stoichiometric matrices. Below is an overview of the organization of the Data folder.

🔹 ENGRO2 Graph
Stoichiometric matrix file
(Extracted using COBRApy functions from the SBML model)

Feature folder
Contains various flux sampling and sensitivity analyses:

All sampled fluxes (CHRR)
All sampled fluxes (CBS)
Sampled statistics (mean, median, mode) - CBS
Sampled statistics (mean, median, mode) - CHRR
Sensitivity analysis - CBS
Sensitivity analysis - CHRR
Knockout (KO) simulation results
Label folder

CERES normalized scores
GECKO normalized scores
🔹 RECON 3D Graph (genome-wide)
Stoichiometric matrix file
(Extracted using COBRApy functions from the SBML model)

Feature folder

All sampled fluxes (CHRR)
All sampled fluxes (CBS)
Sampled statistics (mean, median, mode) - CBS
Sampled statistics (mean, median, mode) - CHRR
Sensitivity analysis - CBS
Sensitivity analysis - CHRR
KO simulation results
Label folder

CERES normalized scores
GECKO normalized scores
