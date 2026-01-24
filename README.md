# G-Quadruplex Biophysical Analysis

**Author:** James Lau Yi Wei  
**Programmin Language:** R  
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Overview

This repository contains the complete R-based analytical codebase developed for an MPharm final-year research project investigating the biophysical stabilisation of G-quadruplex DNA by small-molecule ligands and the resulting crystallisation behaviour.

This repository includes R code for:
- Circular Dichroism (CD) thermodynamic analysis
- Non-parametric statistical comparison of ligand-induced stabilisation
- Quantitative analysis and visualisation of crystallisation outcomes
All scripts were written to support mechanistic interpretation, reproducibility, and publication-quality reporting.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Repository Scope
This repository includes all analytical workflows used in the project:
- CD thermal melting and thermodynamic modelling  
- Statistical comparison of ligand-induced ΔTm values  
- Crystallisation outcome categorisation and visualisation  
- Together, these scripts form the quantitative backbone of the project.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## 1. CD Thermodynamic Analysis
### Purpose: To quantify ligand-induced stabilisation of G-quadruplex DNA using CD thermal melting experiments, extracting apparent thermodynamic parameters under two-state folding assumptions.

### Key Features
- Raw CD CSV cleaning and reshaping  
- Buffer baseline correction  
- Savitzky–Golay smoothing to reduce spectral noise  
- Extraction of characteristic parallel G-quadruplex CD bands (260–270 nm)  
- Non-linear least squares fitting )nls) using the Boltzmann two-state model
- Extraction of:
  - Melting temperature (Tm)
  - Enthalpy change (ΔH)
  - Entropy change (ΔS)
- Calculation of:
  - ΔG(T) across temperature range
  - Equilibrium constant (Keq)
  - Fraction folded at crystallisation-relevant temperatures (e.g. 4 °C, 12 °C)

Assumptions documented within the research paper: 
1.	Structural and folding assumptions: 
  a)	Strictly two-state folding only: The CD signal is a population-weighted average of two states across all structures without any partial folding intermediates, misfolded structures or interconversion of G-quadruplex topologies.  
  b)	Single dominant cooperative transition occurs without ligand unbinding or step-wise unfolding: The observed CD signal is mainly attributed to global simultaneous unfolding of the G-quadruplex.

2.	Thermodynamic and mathematical assumptions: 
  a)	Linear baselines for folded and unfolded states: With reference to step 3 in the figure 4, the CD signal changes approximately linearly with temperature. 
  b)	Enthalpy (ΔH) and entropy (ΔS) of the G-quadruplex is always temperature-independent: Across the measured temperature range, there is assumed to be negligible change in the G-quadruplex structure’s heat capacity (ΔCₚ ≈ 0), such that enthalpy and entropy differences in the folded and unfolded state remain constant. This follows the typical van’t Hoff description in which the unfolding equilibrium demonstrates a linear dependence of ln K vs 1/T within the experimentally accessible temperature range.

3.	Experimental validity and interpretation assumptions: 
  a)	The CD signal measured is a population-weighted average of only the folded and unfolded molecules: The CD only measures the fraction of folded or unfolded G-quadruplex structures within the population. Misfolded configurations, if present are assumed to be negligible or spectroscopically indistinguishable from the folded state and are thus not accounted for. 
  b)	Reversible equilibrium between the folded and unfolded state and the equilibrium constant: At each temperature interval, the G-quadruplexes have been given adequate time to establish its equilibrium state (K(T)) between folded and unfolded state, ensuring that the derived Tm is meaningful.

As a result, all thermodynamic parameters are treated as apparent values.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## 2. Statistical Comparison of Ligand-Induced Stabilisation
### Purpose: To statistically compare ligand-induced changes in melting temperature (ΔTm) between two G-quadruplex ligands (QN-302 and CM-03) across multiple sequences that satisfy the two-state assumption.

### Methodology: 
- ΔTm calculated relative to apo DNA for each sequence  
- Paired Wilcoxon signed-rank test used due to:
  - Small sample size
  - Non-normal distribution
  - Paired experimental design
- Exact p-value and confidence intervals reported

### Interpretation
The analysis evaluates:
- Directionality of stabilisation
- Median and mean ΔTm differences
- Statistical power limitations inherent to small-n biophysical datasets
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## 3. Crystallisation Outcome Analysis and Visualisation
### Purpose: To quantify and visualise crystallisation outcomes across different chemical conditions used during screening experiments.

### Workflow
- Crystallisation outcomes categorised as:
  - Distinct crystals
  - Crystalline precipitate
  - Amorphous precipitate / phase separation
  - Clear / no result
- Results reshaped into long format for plotting
- Stacked bar plots generated using ggplot2 with:
  - Controlled factor ordering
  - Custom colour palettes
  - Publication-ready formatting

This analysis enables direct comparison of condition efficacy and supports rational optimisation of crystallisation strategies.


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Notes
1. This repository may be suitable for:
  - G-quadruplex stability studies
  - Ligand-induced DNA folding analysis
  - Supporting crystallisation decision-making
  - Reuse or extension in structural or chemical biology projects

2. This codebase emphasises:
  - Transparency of assumptions
  - Reproducibility
  - Physical interpretability of outputs
  - Clear separation between data processing, modelling, and visualisation

3. Code is modular and may be adapted to related nucleic acid systems

4. Figures generated are formatted for direct inclusion into reports or manuscripts
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
