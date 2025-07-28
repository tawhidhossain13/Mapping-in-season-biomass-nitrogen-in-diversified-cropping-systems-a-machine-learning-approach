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
│   ├── rasters/                # PlanetScope and Sentinel-2 images, DEM, SWC (as .tif)
│   ├── shapefiles/             # Field boundaries, clusters, etc. (.shp, .shx, .dbf, .prj)
│   └── Dat_IPP-N_TH.xlsx       # Ground truth biomass and nitrogen data
├── notebooks/
│   ├── 2nd_paper_RF.ipynb      # Random Forest models (with/without soil data)
│   ├── 2nd_paper_XGB.ipynb     # XGBoost models
│   └── 2nd_paper_map_production_best_models.ipynb  # Generating spatial prediction maps
├── README.md                   # Project overview and instructions
└── requirements.txt            # Python packages used
```

---

## 🧪 Key Models

- **RF-2**: Random Forest model predicting biomass nitrogen **without soil variables** (best performance)
- **RF-4**: Random Forest model predicting above-ground biomass **without soil variables**
- **XGB-1 to XGB-4**: Alternative XGBoost models (slightly lower accuracy)

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
Email: your_email@example.com  
GitHub: your_github_username

---

## 📄 License

This repository is available for non-commercial academic use. Please contact the authors if you intend to reuse the data or code for commercial applications.
