# wildfires-portugal-smartcities
data science lab on smart cities final project

# Wildfires in Portugal — Smart Cities Final Project

**Data Science for Smart Cities** | Università degli studi di Milano-Bicocca  
Inês Maneta · João Pedro Sousa · Marta Dias · Rita Pinto

---

## Overview

This project investigates whether wildfire prevention infrastructure in Portugal is distributed equitably, and whether the most socially vulnerable municipalities face both the highest fire risk and the greatest coverage gaps.

Using open geospatial data from ICNF (Instituto da Conservação da Natureza e das Florestas), we build a national-scale wildfire risk model, measure how well the existing primary fuel-management network covers the highest-risk zones, and overlay the results with social vulnerability indicators to identify priority areas for policy intervention.

The full analysis is implemented in Python.

---

## Research Question

> *How effectively does Portugal's primary fuel management infrastructure cover high wildfire risk zones, are the gaps in prevention coverage disproportionately concentrated in the most socially vulnerable municipalities, and what targeted policy interventions could address these inequalities?*

---

## Repository Structure

```
wildfires-portugal-smartcities/
│
├── data/
│   ├── raw/               # Original ICNF datasets (see Data Sources below)
│   └── processed/         # Outputs from preprocessing scripts
│
├── notebooks/             # Jupyter notebooks (one per analysis step)
│
├── outputs/               # Final maps and figures used in the essay
│
├── essay/                 # LaTeX source files
│
├── requirements.txt       # Python dependencies
└── README.md
```

---

## Data Sources

All datasets are publicly available from ICNF and INE. Download them and place them in `data/raw/`.

| Dataset | Source | Description |
|---|---|---|
| Burned areas 2021–2024 | [ICNF](https://www.icnf.pt) | Annual fire perimeters |
| Conjunctural hazard maps 2021–2024 | [ICNF](https://www.icnf.pt) | Climate-driven fire danger rasters |
| Critical fire locations | [ICNF](https://www.icnf.pt) | Structurally fire-prone areas |
| Vegetation index (NDVI) | [ICNF](https://www.icnf.pt) | Fuel availability |
| Aridity index | [ICNF](https://www.icnf.pt) | Fuel desiccation conditions |
| Primary fuel-management network | [ICNF](https://www.icnf.pt) | Prevention infrastructure |
| Municipality boundaries | [ArcGIS / ICNF](https://www.icnf.pt) | Study area limits |
| Social vulnerability indicators | [INE](https://www.ine.pt) | Population age, density, income by municipality |

> ⚠️ Raw data files are not tracked in this repository due to file size. Please download them directly from the sources above.

---

## Setup

**1. Clone the repository**
```bash
git clone https://github.com/martarpdias/wildfires-portugal-smartcities.git
cd wildfires-portugal-smartcities
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Download the data** from the sources above and place the files in `data/raw/`

**4. Run the notebooks** in order (see Analysis Pipeline below)

---

## Analysis Pipeline

| Step | Notebook | Description |
|---|---|---|
| 1 | `01_risk_model.ipynb` | Build the national wildfire risk map (weighted overlay) |
| 2 | `02_temporal_analysis.ipynb` | Spatio-temporal analysis of burned areas 2021–2024 |
| 3 | `03_coverage_gaps.ipynb` | Measure fuel-management network coverage per municipality |
| 4 | `04_social_vulnerability.ipynb` | Build the social vulnerability index from INE data |
| 5 | `05_clustering.ipynb` | K-means clustering: risk × coverage gap × vulnerability |
| 6 | `06_visualisations.ipynb` | Final maps and figures for the essay |

---

## Requirements

See `requirements.txt`. Main libraries:

- `geopandas` — spatial data handling
- `rasterio` — raster processing
- `numpy` — array operations and weighted overlay
- `matplotlib` + `contextily` — mapping and visualisation
- `scikit-learn` — K-means clustering
- `scipy` — statistical analysis
- `jupyter` — notebooks

---

## Note on AI Usage

In line with the course guidelines, generative AI (Claude by Anthropic) was used for grammar and text refinement and as a support tool in the implementation of code. All analytical decisions, interpretations and written content were produced by the authors.

---

## License

This project is for academic purposes only.
