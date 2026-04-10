# Reproducibility

This document describes how to reproduce the main dataset and results provided in this repository.

## 1. Install dependencies

Install the required Python packages listed in `requirements.txt`.

```bash
pip install -r requirements.txt
````

## 2. Prepare the source data

Some raw source datasets are not fully redistributed in this repository because of their large file size and the access policies of the original data providers.

Users should obtain the required source data from the official providers before running the workflow.

### Required source datasets

* **OCO-2/OCO-3 Lite products** — NASA GES DISC
* **CAMS greenhouse gas inversion product** — Copernicus Atmosphere Data Store (ADS)
* **TCCON observations**
* **WDCGG observations**

### Suggested local directories

After downloading, the source data are recommended to be placed in:

* `data/cams/raw`
* `data/ground_obs/TCCON/raw`
* `data/ground_obs/WDCGG/raw`
* `data/Satellite/raw/oco2`
* `data/Satellite/raw/oco3`

## 3. Run the workflow

Run the notebooks in the following order:

1. `src/step01_data_preprocessing.ipynb`
2. `src/step02_stk_reconstruction.ipynb`
3. `src/step03_technical_validation.ipynb`
4. `src/step04_spatiotemporal_patterns.ipynb`

## 4. Main outputs

The main outputs are stored in:

* `output/oco2_xco2_month_2015_2024_stk_SEA.nc`
* `output/Validation/`
* `output/trend/`

## 5. Notes

* Users should follow the data-use and citation requirements of the original data providers.
* Local file paths in the notebooks may need to be adjusted depending on the computing environment.
* The `output/` directory contains the reconstructed dataset, validation outputs, and trend analysis results.
