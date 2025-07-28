# Mapping In-Season Biomass Nitrogen in Diversified Cropping Systems

This repository contains the data, code, and models used in our study titled:  
**"Mapping in-season biomass nitrogen in diversified cropping systems: a machine learning approach"**  
*(submitted to the European Journal of Remote Sensing)*

---

## 🌱 Overview

This project uses high-resolution satellite imagery, soil, topographic, climate, and phenological data to predict above-ground biomass and biomass nitrogen (Bio_N) across six crops: barley, rye, wheat, rapeseed, maize, and sunflower. We employ machine learning models (Random Forest and XGBoost) to map crop-specific nitrogen status in a diversified field landscape in Brandenburg, Germany (2021–2024).

---

## 📁 Repository Structure

```
.
├── data/
│   ├── rasters/                # PlanetScope, DEM,slope,aspect (as .tif) for producing maps using trained model
│   ├── shapefiles/             # Field boundaries, clusters, etc. (.shp, .shx, .dbf, .prj)
│   └── Dat_IPP-N_TH.xlsx       # Ground truth biomass and nitrogen data, the main dataset used for developing the model
├── notebooks/
│   ├── 2nd_paper_RF.ipynb      # Random Forest models (with/without soil data): in the workflow, it might be possible that soil variables are not included in the currrent set up, but user can load them by typing the variables name
│   ├── 2nd_paper_XGB.ipynb     # XGBoost models: in the workflow, it might be possible that soil variables are not included in the currrent set up, but user can load them by typing the variables name
│   └── 2nd_paper_map_production_best_models.ipynb  # Generating spatial prediction maps for a any specific dates using single planet imagery, corresponding crop and climate variable values and topographic variables.
├── README.md                   # Project overview and instructions
└── requirements.txt            # Python packages used
```

---

## 🧪 Key Models

- RF-1 and XGB-1 predict biomass N and include soil variables.
- RF-2 and XGB-2 predict biomass N but exclude soil variables.
- RF-3 and XGB-3 predict above-ground biomass and include soil variables.
- RF-4 and XGB-4 predict above-ground biomass but exclude soil variables.
- <img width="930" height="547" alt="image" src="https://github.com/user-attachments/assets/196ecc36-7f59-408c-b76e-7665e4c8b3c0" />

These model labels will be used consistently throughout the following sections to distinguish between prediction targets and the inclusion or exclusion of soil data.

All models were trained with spatial cross-validation using **KMeans clustering** to ensure independence between training and test sets.

---

## 🚀 How to Reproduce the Workflow

1. Clone this repo or download as ZIP.
2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Open any of the Jupyter notebooks in the `/notebooks/` folder:

   - `2nd_paper_RF.ipynb`
   - `2nd_paper_XGB.ipynb`
   - `2nd_paper_map_production_best_models.ipynb`

4. Follow cell-by-cell instructions to:
   - Load data
   - Train/validate models
   - Generate SHAP plots
   - Create Bio_N prediction maps

---

## 📊 Key Results

- **R² = 0.75** for biomass, **R² = 0.65** for nitrogen uptake (best RF models)
- BBCH, NIR reflectance, PAR, and precipitation were the most important predictors
- Soil texture (sand, silt, clay) contributed little to predictive accuracy

---

## 🛰️ Data Sources

- **Imagery**: PlanetScope (3m), Sentinel-2 (10m)
- **Soil Data**: Proximal sensor and Planet SWC product
- **Topography**: DEM from GeoBasis-DE
- **Climate**: Weather station data from patchCROP

---

## 🧾 Citation

If you use this code or data, please cite:

> Hossain et al. (2025) *Mapping in-season biomass nitrogen in diversified cropping systems: a machine learning approach*. European Journal of Remote Sensing (under review).

---

## 👨‍🔬 Contact

**Md Tawhid Hossain**  
Leibniz-Centre for Agricultural Landscape Research (ZALF)  
Email: mdtawhid.hossain@zalf.de or tawhidhossain13@gmail.com  
GitHub: Tawhidhossain13

---

## 📄 License

This repository is available for non-commercial academic use. Please contact the authors if you intend to reuse the data or code for commercial applications.
