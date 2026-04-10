# Reproducibility

This document describes how to reproduce the main dataset and results provided in this repository.

## 1. Install dependencies

Install the required Python packages listed in `requirements.txt`.

```bash
pip install -r requirements.txt
````

## 2. Prepare external data

Prepare the external source data required for running the workflow.

Some raw input datasets are not distributed with this repository because of their large file size and the access policies of the original data providers. Users should obtain these datasets from the official sources before running the notebooks.

The main external source data include:

* OCO-2 Level 2 Lite Full Physics XCO2 product
* OCO-3 Level 2 Lite Full Physics XCO2 product

These external datasets should be downloaded and placed in the appropriate local directories before starting the workflow.

## 3. Repository data organization

The repository includes the following categories of data and outputs:

* `data/cams/`: CAMS background XCO2 data used in the reconstruction workflow
* `data/ground_obs/`: ground-based observations used for technical validation, including TCCON and WDCGG data
* `data/intermediate/`: intermediate files generated during preprocessing, gridding, and monthly adjustment
* `output/dataset/`: final reconstructed monthly XCO2 dataset
* `output/validation/`: matched validation results against OCO-3, TCCON, and WDCGG
* `output/trend/`: trend analysis results
* `output/figures/`: generated figures

## 4. Run data preprocessing

Run `src/step01_data_preprocessing.ipynb` to perform the preprocessing of satellite observations.

This step mainly includes:

* quality control of OCO-2 and OCO-3 observations
* gridding of satellite observations
* monthly adjustment based on the CAMS background time series

Main outputs of this step are stored in:

* `data/intermediate/step01_QA_Control/`
* `data/intermediate/step02_grid/`
* `data/intermediate/step03_Keeling_curve/`

## 5. Run STK reconstruction

Run `src/step02_stk_reconstruction.ipynb` to reconstruct the monthly 0.1° XCO2 dataset using the background-constrained local spatiotemporal kriging method.

Main output of this step:

* `output/dataset/oco2_xco2_month_2015_2024_stk_SEA.nc`

## 6. Run technical validation

Run `src/step03_technical_validation.ipynb` to evaluate the reconstructed dataset against independent or external reference datasets.

This step includes validation against:

* OCO-3
* TCCON
* WDCGG

Main outputs of this step are stored in:

* `output/validation/`

## 7. Run pattern analysis

Run `src/step04_patterns.ipynb` to generate the main figures and statistical summaries of the reconstructed XCO2 dataset.

This step mainly includes:

* regional mean time series analysis
* spatial distribution of multi-year mean XCO2
* spatial distribution of linear change rates

Main outputs of this step are stored in:

* `output/trend/`
* `output/figures/`

## 8. Recommended execution order

To reproduce the main dataset and results, the notebooks should be run in the following order:

1. `src/step01_data_preprocessing.ipynb`
2. `src/step02_stk_reconstruction.ipynb`
3. `src/step03_technical_validation.ipynb`
4. `src/step04_patterns.ipynb`

## 9. Notes

Before running the workflow, users may need to update local file paths in the notebooks according to their own computing environment.

Because different computing environments may use different directory structures, some path variables may need to be modified manually.

The final reconstructed dataset and derived outputs are stored in the `output/` directory.

