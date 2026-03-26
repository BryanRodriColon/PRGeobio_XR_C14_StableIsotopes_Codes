# PRGeobio_XR_C14_StableIsotopes_Codes

## Overview


This repository contains the analytical workflows used for the geochemical, mineralogical, isotopic, and chronological components in support of the manuscript entitled **“Paleoenvironmental Evolution and Geomorphic Controls on Microbialite Distribution in Laguna Providencia, Puerto Rico”**, by **Bryan J. Rodríguez-Colón et al.** The manuscript has been submitted to *Sedimentology* and is also available as a preprint under the same title.




The repository is organized into four main components:

- **XRF_Codes**: preprocessing and multivariate analysis of XRF core-scanning data
- **StableIsotope_Plotting_Codes**: visualization of carbonate and organic stable isotope datasets
- **XRD_Codes**: preprocessing, alignment, visualization, and mineralogical interpretation of diffraction data
- **RadioCarbon_Codes**: radiocarbon calibration and Bayesian age-depth modeling

---

## Repository Structure

```text
PRGeobio_XR_C14_StableIsotopes_Codes/
│
├── XRF_Codes/
│   ├── Code1_clr_XRFcores.Rmd
│   ├── Code2_PCA_XRFcores.Rmd
│   ├── InputData/
│   ├── OutputData/
│   └── RData/
│
├── StableIsotope_Plotting_Codes/
│   ├── Code1_isoCarbs.Rmd
│   ├── Code2_isoOrg.Rmd
│   ├── InputData/
│   ├── OutputData/
│   └── plots/
│
├── XRD_Codes/
│   ├── Code0_XRD_stds.Rmd
│   ├── Code1_XRD_bkg_smooth_data.Rmd
│   ├── Code2_XRD_Alignment_data.Rmd
│   ├── Code3_XRD_Plotting.Rmd
│   ├── Code4_XRD_MolperMgCa.Rmd
│   ├── InputData/
│   ├── OutputData/
│   └── RData/
│
├── RadioCarbon_Codes/
│   ├── Code1_age_calibration.Rmd
│   ├── Code2_Bacon_SedRates.Rmd
│   ├── InputData/
│   ├── OutputData/
│   └── Bacon_runs/
│
└── README.md
```
## XRF_Codes

This subfolder contains the workflow used to preprocess and analyze XRF-derived elemental count data from sediment cores C2 and C3.

### Code1_clr_XRFcores
This script imports elemental count data, applies quality-control filtering, and performs centered log-ratio (clr) transformation to prepare the compositional data for multivariate analysis. The workflow addresses common issues in XRF datasets, including zeros, sparsity, low-count elements, and closure effects. Processed clr-transformed datasets are exported for downstream use.

### Code2_PCA_XRFcores
This script performs principal component analysis on the clr-transformed XRF datasets. It generates PCA scores, loadings, scree plots, and facies-based visualizations for cores C2 and C3. Stratigraphic facies are assigned by depth interval to support paleoenvironmental interpretation of the dominant geochemical gradients.

### Main outputs
- clr-transformed XRF datasets
- PCA scores and loadings
- Scree plots
- PCA figures and exported summary objects

### Important packages
- `dplyr`
- `ggplot2`
- `compositions`
- `zCompositions`
- `plotly`
- `ggrepel`

---

## StableIsotope_Plotting_Codes

This subfolder contains the plotting workflows for carbonate and organic stable isotope datasets from the Guánica lagoon system.

### Code1_isoCarbs
This script generates carbonate stable isotope crossplots of δ¹³C versus δ¹⁸O for sediment, microbialite, beach sand, and Ponce Limestone samples. It produces static publication-quality plots and interactive exploratory versions. These figures support interpretation of carbonate geochemistry and are included as appendix-style supporting material for the dissertation chapter.

### Code2_isoOrg
This script processes and visualizes organic geochemical data, primarily δ¹³Corg and TOC/TN ratios, from sediment cores and microbialite samples. It generates manuscript-quality and interactive crossplots used to evaluate organic matter sources and paleoenvironmental conditions. It also includes statistical comparison of overwash-related deposits against other stratigraphic intervals.

### Main outputs
- Carbonate isotope crossplots
- Organic isotope and TOC/TN crossplots
- Interactive HTML plots
- Static SVG and TIFF figures

### Important packages
- `ggplot2`
- `plotly`
- `dplyr`

---

## XRD_Codes

This subfolder contains the XRD workflow used to prepare mineral standards, preprocess diffraction data, align patterns, visualize spectra, and estimate carbonate Mg content.

### Code0_XRD_stds
This script prepares mineral standards and quality-control mixtures used for XRD interpretation. It converts reference d-spacings to 2θ values, applies wavelength transformation, and compiles processed mineral libraries for downstream comparison and identification.

### Code1_XRD_bkg_smooth_data
This script performs the main preprocessing of raw XRD spectra, including wavelength transformation from Co to Cu, background subtraction, smoothing, and correction of dataset-specific acquisition artifacts. It prepares the diffraction patterns for alignment and interpretation.

### Code2_XRD_Alignment_data
This script aligns diffraction patterns using internal mineral anchors, primarily halite and secondarily aragonite. The goal is to correct positional offsets in 2θ and ensure internal consistency across all samples before mineralogical interpretation.

### Code3_XRD_Plotting
This script visualizes aligned XRD spectra and mineral standards using powdR and custom plotting approaches. It supports comparison among samples and export of publication-quality diffraction pattern figures.

### Code4_XRD_MolperMgCa
This script estimates mol% MgCO₃ in carbonate minerals using empirical relationships between d-spacing and Mg substitution. It is used to classify calcite phases and evaluate carbonate mineral chemistry in support of sedimentological and petrographic interpretation.

### Main outputs
- Processed mineral standards and QC datasets
- Background-corrected and smoothed spectra
- Aligned diffraction patterns
- XRD plots
- MgCO₃ and CaCO₃ estimates for carbonate phases

### Important packages
- `powdR`
- `ggplot2`
- `dplyr`

---

## RadioCarbon_Codes

This subfolder contains the chronological workflow for individual radiocarbon calibration and Bayesian age-depth modeling.

### Code1_age_calibration
This script calibrates individual radiocarbon ages from sediment cores LPC2 and LPC3 using the `IntCal` package. Terrestrial materials are calibrated with IntCal20, whereas sediment organic carbon samples are calibrated with Marine20 using a regional reservoir correction (ΔR = 137 ± 20 years). The script extracts posterior median, mean, and 95% HPD ranges, converts ages from cal BP to CE/BCE notation, and exports calibrated age tables. Calibration plots were generated using the native `IntCal` plotting interface and saved manually.

### Code2_Bacon_SedRates
This script performs Bayesian age-depth modeling using the `rbacon` package and extracts sedimentation rates for cores LPC2 and LPC3. It summarizes accumulation-rate outputs, converts them to sedimentation rates in mm/yr, reconstructs depth intervals, and generates depth-resolved sedimentation-rate plots.

### Main outputs
- Calibrated radiocarbon age tables
- Age-depth models
- Sedimentation-rate summaries
- Sedimentation-rate figures

### Important packages
- `IntCal`
- `rbacon`
- `dplyr`
- `tidyr`
- `ggplot2`

---

## General Notes

- All workflows were developed for dissertation research on Laguna Providencia and associated coastal lagoon systems in southwestern Puerto Rico.
- Some scripts, particularly within the XRD workflow, also include related datasets used in parallel dissertation chapters and associated manuscripts.
- Final figure formatting in some cases was refined in Adobe Illustrator after export. These edits did not alter the underlying analytical results.
- Calibration plots for the radiocarbon workflow were saved manually using the native `IntCal` plotting interface.
- Some preprocessing decisions are dataset-specific and should be carefully reviewed before applying these scripts to other projects.
- In the code and data files provided in this repository, the abbreviations **PO**, **JB**, and **PS** are used to denote the three lagoon systems analyzed in this study (PO = Salinas Vernales, JB = Salinas Salinetas, PS = Laguna Providencia).
In the manuscripts and dissertation, these systems are referred to using a different set of abbreviations (**SV-**, **SS-**, and **LP-**, respectively). This difference reflects an update in nomenclature adopted during manuscript preparation and does not affect the underlying data structure or analyses.
- The sediment core XRf data processing were performed using MATLAB-based scripts developed by a collaborator. As these codes are not original to this repository, they are not included here.


## Authorship and Code Development

These scripts were compiled and written by **Bryan J. Rodríguez-Colón**, with  assistance from AI tools including **ChatGPT-4o** and **ChatGPT-5**, primarily for code structuring, debugging, and documentation.


## Intended Use

This repository is provided to support reproducibility and methodological transparency. Users interested in reusing or adapting these scripts should consult the manuscript methods section for additional contextual details regarding experimental design, sequencing, and analytical rationale.




## Citations

- Arvidson, R. S., & Mackenzie, F. T. (1999). The dolomite problem: Control of precipitation kinetics by temperature and saturation state. *American Journal of Science*.
- Bertrand, S., Tjallingii, R., Kylander, M. E., Wilhelm, B., Roberts, S. J., et al. (2024). Inorganic geochemistry of lake sediments: A review of analytical techniques and guidelines for data interpretation. *Earth-Science Reviews*, 249, 104639.
- Blaauw, M., & Christen, J. A. (2011). Flexible paleoclimate age-depth models using an autoregressive gamma process. *Quaternary Geochronology*, 6, 457–474.
- Khan, N. S., et al. (2019). The application of δ¹³C, TOC and C/N geochemistry of mangrove sediments to reconstruct Holocene paleoenvironments and relative sea levels, Puerto Rico. *Marine Geology*, 415.
- Lamb, A. L., Wilson, G. P., & Leng, M. J. (2006). A review of coastal palaeoclimate and relative sea-level reconstructions using δ¹³C and C/N ratios in organic material. *Earth-Science Reviews*, 75, 29–57.
- Lumsden, D. N., & Chimahusky, J. S. (1980). Relationship between dolomite nonstoichiometry and carbonate facies parameters. *Journal of Sedimentary Petrology*.
- Reimer, P. J., et al. (2020). The IntCal20 Northern Hemisphere radiocarbon age calibration curve (0–55 cal kBP). *Radiocarbon*, 62, 725–757.
- Butler, B.M. and Hillier, S. (2021) powdR: An R package for quantitative mineralogy using full pattern summation of X-ray powder diffraction data. *Computers & Geosciences*, 147, 104662.
