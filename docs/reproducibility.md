````markdown
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

These external datasets should be prepared locally before running the workflow.

## 3. Repository data organization

The repository currently includes the following main directories:

* `data/cams/`: CAMS background XCO2 data
* `data/ground_obs/`: ground-based observations used for validation, including TCCON and WDCGG data
* `data/Satellite/step01_QA_Control/`: quality-controlled OCO-2 and OCO-3 tabular files
* `data/Satellite/step02_grid/`: gridded daily OCO-2 and OCO-3 XCO2 data
* `data/Satellite/step03_Keeling_curve/`: monthly adjusted OCO-2 and OCO-3 XCO2 data
* `output/`: reconstructed dataset, trend analysis results, and validation outputs
* `docs/`: figures and supplementary documentation
* `src/`: main processing notebooks

## 4. Run data preprocessing

Run `src/step01_data_preprocessing.ipynb` to perform the preprocessing of satellite observations.

This step mainly includes:

* quality control of OCO-2 and OCO-3 observations
* gridding of satellite observations
* monthly adjustment based on the CAMS background time series

Main outputs of this step are stored in:

* `data/Satellite/step01_QA_Control/`
* `data/Satellite/step02_grid/`
* `data/Satellite/step03_Keeling_curve/`

## 5. Run STK reconstruction

Run `src/step02_stk_reconstruction.ipynb` to reconstruct the monthly 0.1° XCO2 dataset using the background-constrained local spatiotemporal kriging method.

Main output of this step:

* `output/oco2_xco2_month_2015_2024_stk_SEA.nc`

## 6. Run technical validation

Run `src/step03_technical_validation.ipynb` to evaluate the reconstructed dataset against reference observations.

This step includes validation against:

* OCO-3
* TCCON
* WDCGG

Main outputs of this step are stored in:

* `output/Validation/`

## 7. Run spatiotemporal pattern analysis

Run `src/step04_spatiotemporal_patterns.ipynb` to generate the main figures and statistical summaries of the reconstructed XCO2 dataset.

This step mainly includes:

* regional mean time series analysis
* spatial distribution of multi-year mean XCO2
* spatial distribution of linear change rates

Main outputs of this step are stored in:

* `output/trend/`

## 8. Recommended execution order

To reproduce the main dataset and results, the notebooks should be run in the following order:

1. `src/step01_data_preprocessing.ipynb`
2. `src/step02_stk_reconstruction.ipynb`
3. `src/step03_technical_validation.ipynb`
4. `src/step04_spatiotemporal_patterns.ipynb`

## 9. Notes

Before running the workflow, users may need to update local file paths in the notebooks according to their own computing environment.

Because different computing environments may use different directory structures, some path variables may need to be modified manually.

The final reconstructed dataset, validation outputs, and trend analysis results are stored in the `output/` directory.

