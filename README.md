# Reproducible Data Access for Emerging Contaminants Research
**Author:** Robel Sahilu Bekele  
**Doctoral Researcher**  
Water, Energy and Environmental Engineering Research Unit  
Faculty of Technology, University of Oulu, Finland  

**Email:** robel.bekele@oulu.fi  
**Phone:** +358 41 329 6301  
**ORCID:** https://orcid.org/0000-0001-5572-5816  

---

## Project Overview

### Problem Statement
Emerging contaminants (ECs) from sanitation systems—including pharmaceuticals, personal care products, industrial chemicals, microbial contaminants, and antimicrobial resistance genes—are increasingly found in surface waters. Conventional wastewater treatment plants (WWTPs) are not engineered to remove these compounds. In Finland, low temperatures and long water residence times further slow degradation, raising concerns about persistence, accumulation, and long-term risks to freshwater quality and drinking water supplies.

### Challenge Statement
This issue remains unresolved due to fragmented monitoring across Finland. Existing studies focus on limited contaminants, restricted sampling frequencies, or isolated WWTPs. Few efforts integrate contaminant effluent loads with downstream fate in freshwater systems or assess implications for drinking water sources. The lack of nationwide, multi-season, multi-technology datasets has prevented a full understanding of contaminant loads, environmental occurrence, and risks.

### Solution Statement
This project provides the first comprehensive dataset combining:
- Effluent loads of **137 emerging contaminants**  
- Multi-season sampling from **6 WWTPs**  
- One-time sampling from **25 WWTPs** across Finland  
- Sampling campaigns in **1 river, 1 lake, and 1 coastal system**  
- Environmental risk assessments using PNEC benchmarks  
- Assessment of EC occurrence in **drinking water sources**  

By linking WWTP discharges with downstream occurrence in freshwater systems, this project bridges critical knowledge gaps regarding transport, transformation, accumulation, and risk.

### Objectives
- Quantify environmental loads of 137 ECs across Finnish WWTPs.
- Assess seasonal and spatial variability across WWTPs of varying sizes and technologies.
- Characterize transport, attenuation, and persistence of ECs in rivers and lakes.
- Evaluate ecological risks using MEC/PNEC ratios.
- Assess occurrence of contaminants in drinking water sources.
- Identify implications for raw water quality and water supply safety.

### Research Questions
- Which ECs consistently appear in WWTP effluents, and how do loads vary by plant type?
- Do seasonal factors affect contaminant loads in repeatedly sampled WWTPs?
- How do contaminants move and transform downstream in rivers and lakes?
- Which ECs pose ecological risk based on RQ (MEC/PNEC)?
- What ECs occur in drinking water sources, and what risks do they indicate?
- What implications do these contaminants have for water supply safety?

---

## Data Sources

### Wastewater Effluent Data
- **25 WWTPs**, including:
  - 6 WWTPs with four-season sampling + one special sampling campaign  
  - 19 WWTPs sampled once (nationwide screening)

### Freshwater Systems  
- 1 river system  
- 1 lake  
- 1 coastal/brackish system influenced by freshwater inflows  

### Analytical Methods  
- Solid Phase Extraction (SPE)  
- Liquid Chromatography–Mass Spectrometry (LC–MS/MS)  
- Flow-adjusted load estimation  
- Ecological risk assessment using PNEC data  
- Statistical analyses (PCA, cluster analysis, correlations, left‑censored methods, etc.)

---

## Data Used in SE1 Assignment

### 1. Synthetic Dataset (Required by SE1)
Created in the notebook using a fixed random seed.  
Uploaded to Zenodo:  
👉 https://zenodo.org/records/19180916

### 2. Zenodo Data Access  
Downloaded programmatically in `SE1_data_access.ipynb` using a stable URL.

### 3. API‑Based Geospatial Data  
Accessed using the Overpass API (OpenStreetMap) for water features in Oulu region.  
Saved to `data/raw/osm_water_features.geojson`.

### 4. Storage Location  
All raw datasets saved in:  
``
## README Update for SE3 Assignment
# README – Standard Element 3## Model Training, Validation, and Interpretation

**Author:** Robel Sahilu Bekele  
Doctoral Researcher, Water, Energy and Environmental Engineering Research Unit  
Faculty of Technology, University of Oulu, Finland  
Email: robel.bekele@oulu.fi  
ORCID: https://orcid.org/0000-0001-5572-5816  

---

## Purpose of This Analysis

This analysis addresses **Standard Element 3** by training, validating, and
interpreting statistical models to evaluate the effects of **season** and
**wastewater treatment technology** on effluent concentrations of emerging
contaminants measured at multiple wastewater treatment plants (WWTPs).

---

## Input Data

The statistical models use a locally stored, processed dataset containing
contaminant concentrations and associated metadata:

- `data/processed/Apland_data_6WWTPs_Eff.csv`

The dataset includes:
- Yeo–Johnson–transformable contaminant concentration variables
- Sampling season
- WWTP identifier
- Treatment technology type

---

## Modeling Workflow

The modeling workflow is organized into the following steps:

### 1. Distribution assessment and transformation
- Shapiro–Wilk tests are applied to evaluate normal and lognormal distributions.
- Yeo–Johnson transformations are applied to contaminant concentrations to
  stabilize variance and improve normality prior to modeling.

### 2. Statistical model training
- One **linear mixed‑effects model (LMM)** is fitted per contaminant.
- Fixed effects:
  - Season  
  - Treatment technology
- Random effect:
  - WWTP (random intercept)
- Models are estimated using restricted maximum likelihood (REML).

### 3. Model output extraction and interpretation
- Fixed‑effect coefficients and p‑values are extracted from each model.
- Seasonal and technology effects are summarized across contaminants.
- Results are further summarized for a subset of eight EU UWWTD indicator
  compounds.

### 4. Model fit evaluation
- Model performance is quantified using:
  - Marginal R² (variance explained by fixed effects)
  - Conditional R² (variance explained by fixed and random effects)
  - Akaike Information Criterion (AIC)

### 5. Supplementary multivariate analysis
- Principal component analysis (PCA) and heatmaps are applied to the transformed
  dataset to explore patterns of co‑occurrence and WWTP similarity.

---

## Outputs

The analysis produces the following outputs:

### Tables
- `outputs/model_fit_coefficients.csv`  
- `outputs/LMM_summary_all_contaminants.csv`  
- `outputs/LMM_summary_EU_indicators.csv`

### Figures
- PCA score plots
- Heatmaps of mean transformed contaminant concentrations per WWTP

---

## Software

All analyses were conducted in **R**, using the following key packages:
- `readr`
- `broom`
- `ggplot2`
- `pheatmap`
- `dplyr`

---

## Notes

This README documents the **statistical modeling workflow** for Standard
Element 3 and complements the detailed Data and Methods document and Results
section developed at this stage of the analysis.