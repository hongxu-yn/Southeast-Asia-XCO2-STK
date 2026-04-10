# Reproducibility

This document provides a step-by-step guide to reproducing the datasets and analysis results presented in this repository.

---

## 1. Install Dependencies

Ensure you have Python installed (preferably version 3.8 or higher). Install the necessary libraries using the provided `requirements.txt` file:

```bash
pip install -r requirements.txt
```

---

## 2. Prepare Source Data

Due to licensing policies and large file sizes, raw source datasets are not redistributed in this repository. You must download these directly from the official providers.

### Required Source Datasets

| Dataset | Provider | Access Link |
| :--- | :--- | :--- |
| **NASA OCO-2 & OCO-3 Lite** | NASA GES DISC | [Search OCO Data](https://disc.gsfc.nasa.gov/datasets?keywords=OCO-2%20OCO-3%20Lite) |
| **CAMS GHG Inversion** | Copernicus ADS | [CAMS Global Inversion](https://ads.atmosphere.copernicus.eu/datasets/cams-global-greenhouse-gas-inversion) |
| **TCCON Observations** | TCCON Archive | [tccondata.org](https://tccondata.org/) |
| **WDCGG Observations** | WMO / JMA | [WDCGG Search](https://gaw.kishou.go.jp/search) |

> **Note:** The **Lite** satellite products are recommended as they include essential bias corrections and data screening for $XCO_2$.

### Suggested Local Directory Structure

To ensure the notebooks run correctly, organize your downloaded data into the following structure:

```text
data/
├── cams/
│   └── raw/
├── ground_obs/
│   ├── TCCON/
│   │   └── raw/
│   └── WDCGG/
│       └── raw/
└── Satellite/
    └── raw/
        ├── oco2/
        └── oco3/
```

---

## 3. Run the Workflow

The analysis is divided into sequential Jupyter notebooks. Please execute them in the following order:

1.  **`src/step01_data_preprocessing.ipynb`**: Cleans and formats raw satellite and ground data.
2.  **`src/step02_stk_reconstruction.ipynb`**: Performs the spatiotemporal reconstruction of the $XCO_2$ fields.
3.  **`src/step03_technical_validation.ipynb`**: Compares results against TCCON and WDCGG ground-truth.
4.  **`src/step04_spatiotemporal_patterns.ipynb`**: Generates final figures and trend analysis.

---

## 4. Main Outputs

After completion, the primary results will be generated in the `output/` directory:

*   **Reconstructed Dataset:** `output/oco2_xco2_month_2015_2024_stk_SEA.nc` (NetCDF format)
*   **Validation Reports:** Found in `output/Validation/`
*   **Trend Analysis:** Visualizations and stats in `output/trend/`

---

## 5. Usage Notes

*   **Data Citations:** Users are required to follow the specific citation and data-use policies of NASA, Copernicus, TCCON, and WDCGG.
*   **Path Configuration:** If you choose a different directory structure than suggested in Section 2, you must update the `root_path` or data variables at the beginning of each notebook.
*   **Computational Resources:** The reconstruction step (Step 02) can be memory-intensive; a minimum of 16GB RAM is recommended.
