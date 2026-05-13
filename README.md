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
Emerging contaminants (ECs) from sanitation systems - including pharmaceuticals, personal care products, industrial chemicals, microbial contaminants, and antimicrobial resistance genes - are increasingly found in surface waters. Conventional wastewater treatment plants (WWTPs) are not engineered to remove these compounds. In Finland, low temperatures and long water residence times further slow degradation, raising concerns about persistence, accumulation, and long-term risks to freshwater quality and drinking water supplies.

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

### Freshwater Systems  
- 60 drinking water utilities across Finland  

### Analytical Methods  
- Solid Phase Extraction (SPE)  
- Liquid Chromatography–Mass Spectrometry (LC–MS/MS)  
- Flow-adjusted load estimation  
- Ecological risk assessment using PNEC data  
- Statistical analyses (PCA, cluster analysis, correlations, left‑censored methods, etc.)

---

## Data Access

### 1. Dummy Data created (will be replaced by actual data in the future)
Uploaded to Zenodo:  
👉 https://zenodo.org/records/20133943

### 2. Zenodo Data Access  
Downloaded programmatically in `SE1_data_access_modified.ipynb` using a stable URL.


## Data Processing
- The raw data were cleaned and formatted to ensure consistency and suitability for analysis. Missing values and irrelevant records checked (if any).

## Model Training, Validation, and Interpretation

### Input Data

The statistical models use a locally stored, processed dataset containing
contaminant concentrations and associated metadata:

- `data/processed/analysis_ready_MPs_data.csv`

The dataset includes:
- log transformed contaminant concentration variables
- Sampling season
- WWTP identifier
- Treatment technology type

---

### Modeling Workflow

The modeling workflow is organized into the following steps:

#### 1. Data transformation and preparation
- Contaminant concentration data were log10-transformed (log10(x + 1)) to reduce skewness and stabilize variance prior to modeling.
- Relevant variables, including season, wastewater treatment plant (WWTP), and treatment technology, were converted to categorical (factor) variables.


#### 2. Statistical model training
- A separate **linear model (LM)** was fitted for each contaminant.
- Each model included:
  - Season
  - Treatment technology (Tech_type)
  - WWTP (included as a fixed effect)
- Models were fitted using ordinary least squares (OLS).


#### 3. Model output extraction and interpretation
- Model coefficients and p-values were extracted for each contaminant using tidy outputs.
- Statistical significance of seasonal and treatment technology effects was assessed.
- Summary tables were created to indicate whether these factors significantly influence contaminant concentrations.


#### 4. Model fit evaluation
- Model performance was assessed using:
  - R² (variance explained by the model)
  - Adjusted R²
  - Akaike Information Criterion (AIC)


#### 5. Supplementary multivariate analysis
- Principal component analysis (PCA) and heatmaps are applied to the transformed
  dataset to explore patterns of co‑occurrence and WWTP similarity.

---

### Outputs

The analysis produces the following outputs:

### Tables
- Summary table of statistical significance for season and treatment effects across contaminants  
- Model performance metrics (R², adjusted R², AIC) for each contaminant 


### Software

All analyses were conducted in **R**, using the following key packages:
- `readr`
- `broom`
- `ggplot2`
- `pheatmap`
- `dplyr`

---

## Visualization

### Figures
- PCA score plots
- Heatmaps of mean transformed contaminant concentrations per WWTP

---
