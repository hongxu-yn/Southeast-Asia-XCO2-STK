# Southeast-Asia-XCO2-STK: Spatio-Temporal Reconstructed Dataset

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hongxu-yn/Southeast-Asia-XCO2-STK/blob/main/src/1_Data_Process.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Project Overview

This project provides a seamless monthly high-resolution (**0.1° × 0.1°**) dataset of **column-averaged dry-air mole fraction of carbon dioxide ($XCO_2$)** over South China and Southeast Asia.

Because persistent cloud cover in tropical Southeast Asia causes substantial missing satellite observations, an **adaptive local spatio-temporal kriging (STK)** method was developed to integrate **OCO-2/3** satellite observations with the **CAMS optimized inversion background field**. The resulting dataset is spatially and temporally continuous, providing a high-quality data foundation for regional carbon cycle studies.

---

## 📊 Data Sources

### 1. Satellite Observations
- **OCO-2/3 Lite Products**  
  NASA Level 2 bias-corrected $XCO_2$ products were used as the primary satellite observations.  
  - **Access**: [NASA GES DISC](https://disc.gsfc.nasa.gov/datasets?keywords=OCO-2%20Lite)

### 2. Background Field
- **CAMS Greenhouse Gas Inversion**  
  The **CAMS global greenhouse gas optimized inversion product** was used as the background field. Compared with ordinary reanalysis products, this dataset is constrained by global observation networks and flux optimization, providing a more physically consistent large-scale background for reconstruction.  
  - **Access**: [Copernicus Atmosphere Data Store (ADS)](https://ads.atmosphere.copernicus.eu/datasets/cams-global-greenhouse-gas-inversion)

### 3. Ground-Based Validation Data
This study combines **TCCON** total-column observations and **WDCGG** surface CO₂ observations for independent external validation.

**Table 1. Details of the TCCON and WDCGG observation sites used for validation.**

| Site   | Country     | Network | Geographic setting      | Lon (°E) | Lat (°N) | Elev. (m) |
|--------|-------------|---------|-------------------------|----------|----------|-----------|
| Hefei  | China       | TCCON   | Urban/suburban plain    | 117.17   | 31.90    | 35        |
| Burgos | Philippines | TCCON   | Coastal/island site     | 120.65   | 18.53    | 49        |
| BKT    | Indonesia   | WDCGG   | Mountain site           | 100.318  | -0.20194 | 864       |
| HKG    | China       | WDCGG   | Coastal urban site      | 114.258  | 22.2095  | 60        |
| HKO    | China       | WDCGG   | Coastal urban site      | 114.173  | 22.312   | 65        |
| LLN    | China       | WDCGG   | High-mountain site      | 120.87   | 23.47    | 2862      |
| HAT    | Japan       | WDCGG   | Remote island site      | 123.809  | 24.0607  | 10        |

*TCCON: Total Carbon Column Observing Network; WDCGG: World Data Centre for Greenhouse Gases.*

#### TCCON Observations
The **GGG2020** version of TCCON observations was used for independent validation.

- **Burgos Station (Philippines)**  
  Represents the tropical core region of Southeast Asia.  
  - DOI: [10.14291/tccon.ggg2020.burgos01.R0](https://doi.org/10.14291/tccon.ggg2020.burgos01.R0)

- **Hefei Station (China)**  
  Represents the northern boundary of the study region and an area influenced by both urban emissions and monsoon circulation.  
  - DOI: [10.14291/tccon.ggg2020.hefei01.R1](https://doi.org/10.14291/tccon.ggg2020.hefei01.R1)

#### WDCGG Observations
High-precision global surface CO₂ observations from WDCGG were used to provide supplementary validation from the near-surface atmospheric perspective.

- **Access**: [WDCGG CO₂ data search](https://gaw.kishou.go.jp/search/gas_species/co2/latest)

---

## 🗺️ Visuals

### Figure 1. Study area
<img src="docs/location.png" width="600" alt="Study Area">

### Figure 2. Workflow
<img src="docs/workflow.png" width="600" alt="Workflow">

---

## 📂 Project Structure

```text
Southeast-Asia-XCO2-STK/
├── docs/                     # Figures and illustrations, e.g., location.png and workflow.png
├── src/                      # Core processing scripts and notebooks
│   └── 1_Data_Process.ipynb  # Full workflow: preprocessing, temporal correction, and STK reconstruction
├── examples/                 # Example scripts or demonstration files
├── data/                     # Input/output data directory (created locally, not tracked)
├── .gitignore                # Excludes large files such as .nc and .csv
└── README.md                 # Project documentation
````

---

## 🚀 Getting Started

### 1. Environment Setup

Install the required Python packages in **Google Colab** or a Linux environment:

```bash
pip install -q netCDF4 joblib tqdm xarray pykrige gstools scipy
pip install -q regionmask geopandas geodatasets cartopy
```

### 2. Clone the Repository

```bash
git clone https://github.com/hongxu-yn/Southeast-Asia-XCO2-STK.git
cd Southeast-Asia-XCO2-STK
mkdir -p data
```

### 3. Fetch Large Assets

Because the full dataset is large, data files are distributed separately.

```bash
wget -O data/assets.zip "https://zenodo.org/records/XXXXXXX/files/assets.zip?download=1"
unzip -q data/assets.zip -d ./data/
```

---

## 📦 Data Availability

Due to the large volume of the reconstructed dataset (**~8 GB**), the full data archive is hosted on **Zenodo**.

* **Access link**: [https://doi.org/10.5281/zenodo.XXXXXXX](https://doi.org/10.5281/zenodo.XXXXXXX)

---

## ✅ Technical Validation

The reconstructed dataset was evaluated against independent **TCCON** observations.

* **Hefei**: $R^2 = 0.981$, $RMSE = 1.27\ \mathrm{ppm}$
* **Burgos**: $R^2 = 0.981$, $RMSE = 0.69\ \mathrm{ppm}$

More detailed validation against additional observations can be included in future updates.

---

## 📖 Citation

If you use this repository or dataset, please cite:

> Shi, X., Zhou, G., Yang, L., Zhang, J., Zhang, M., & Xu, H. (2026). *A seamless monthly 0.1° $XCO_2$ dataset over South China and Southeast Asia derived from OCO-2 observations and CAMS background fields (2015–2024).* Scientific Data (submitted).

---

## 📄 License

This project is licensed under the **MIT License**.

