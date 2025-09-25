# Closed-Loop Discovery of H Spillover-Driven CO2 Reduction in Acidic Electrolyte by Phosphine-Modified Cu

**Code provider:** Yuming Su  
**Research Focus:** Machine learning-driven discovery of phosphine-modified copper catalysts for CO2 electroreduction

## Project Overview

This repository contains the computational codes and experimental data for the closed-loop discovery of hydrogen spillover-driven CO2 reduction catalysts. The project employs machine learning techniques, specifically XGBoost regression with SHAP analysis, to identify optimal phosphine-modified copper catalysts for electrochemical CO2 reduction in acidic electrolytes.

## Repository Structure

### Round 1: Initial Screening (`round1_93molsxtb_pred2460mols/`)

This folder contains the first round of machine learning analysis using 93 molecules for training and predicting properties of 2460 molecules.

#### Key Files:
- **`XGB-R_V5.1.0-Alpha.ipynb`** - Main Jupyter notebook for XGBoost regression analysis
- **`Features_93_45.csv`** - Feature matrix for 93 training molecules (45 features)
- **`Features_2461_45.csv`** - Feature matrix for 2460 prediction molecules (45 features)
- **`Values_True_93.csv`** - Experimental target values for training set
- **`Title_45.csv`** - Feature names and descriptions
- **`240415_2461_updated_correct_rows.csv`** - Updated molecular data with corrections for 2460 new molecules.
- **`副本含P分子-20240513修改.xlsx`** - Excel file containing phosphorus-containing molecules data

### Round 2: Advanced Analysis (`round2/`)

The second round includes two sub-analyses with improved feature selection and model optimization.

#### Round 2.1: 108 Molecules Analysis (`round2.1_108molsg16_pred/`)

**Focus:** Step regression with XGBoost and SHAP analysis for feature importance

##### Key Files:
- **`XGB-Stepregression-SHAP-pred-symV2.2 (1).ipynb`** - Advanced notebook with step regression and SHAP
- **`Features_280_54.csv`** - Extended feature matrix (280 molecules, 54 features)
- **`Values_True_280.csv`** - Target values for 280 molecules
- **`Smiles_280.csv`** - SMILES representations of molecules
- **`Round3-shap_summary_plot.png`** - SHAP feature importance summary

#### Round 2.2: 127 Molecules Analysis (`round2.2_127mols/`)

**Focus:** Final optimization with expanded dataset

##### Key Files:
- **`XGB-Stepregression-symV2-Cokp-Copy1.ipynb`** - Final optimized model
- **`Features_127_54.csv`** - Feature matrix for 127 molecules
- **`Values_True_127.csv`** - Target values
- **`Round4-shap_summary_plot.png`** - Final SHAP analysis
- **SHAP Scatter Plots:** Individual feature impact visualizations
  - `shap_scatter_Atom1_ALIEMinValue.png`
  - `shap_scatter_Atom1_ESPAllArea_Ang_2.png`
  - `shap_scatter_Atom1_LEAEAllAverage.png`
  - `shap_scatter_MolecularSizeMedium.png`
  - `shap_scatter_SurfaceEffAtomNum.png`


##### Results Directory (`Stepreg-XGB_V2.0sym_20240627_111035/`):
- **Key Descriptors and Their Physical Significance:**
  1. **Surface Area Indicator (SurfaceEffAtomNum)** - Counts exposed atoms of the molecule, indicating the available catalytic sites，related to shap_scatter_SurfaceEffAtomNum.png
  2. **Molecular Width** - Measures the size of the molecule, with larger molecular size increasing FE_C2+ due to requirement of sufficient hydrophobic area，related to shap_scatter_MolecularSizeMedium.png
  3. **P-atom Openness (P-atom ESP Area)** - Surface area of the phosphorus atom calculated from molecular electron density isosurface allocation; crowded P atoms increase FE_C2+，related to shap_scatter_Atom1_ESPAllArea_Ang_2.png
  4. **P-atom LEAE** - Averaged local electron attachment energy of P; weak back-bonding (higher LEAE values) increases FE_C2+，related to shap_scatter_Atom1_LEAEAllAverage.png
  5. **P-atom ALIE** - Minimum of averaged local ionization energy of P; contributes very little to the overall performance，related to shap_scatter_Atom1_ALIEMinValue.png
     
## Methodology

### Machine Learning Approach
1. **Algorithm:** XGBoost Regression with step-wise feature selection
2. **Feature Engineering:** 54 molecular descriptors including electronic, geometric, and surface properties
3. **Model Validation:** Cross-validation with multiple train-test splits
4. **Interpretability:** SHAP (SHapley Additive exPlanations) analysis for feature importance

### Key Features Analyzed
- **Electronic Properties:** ESP (Electrostatic Potential) descriptors, HOMO-LUMO gaps
- **Geometric Properties:** Molecular size, surface area, atom positions
- **Surface Properties:** Effective surface atoms, local ionization energies
- **Phosphorus-Specific:** Local electron attachment energies, ESP areas on P atoms


## Usage Instructions

### Prerequisites
- Python 3.x
- Jupyter Notebook
- Required packages: pandas, numpy, scikit-learn, xgboost, shap, matplotlib, seaborn


