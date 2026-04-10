# Variable description

This document describes the main dimensions, coordinates, variables, and metadata of the reconstructed XCO2 dataset provided in this repository.

## Dataset file

- `output/oco2_xco2_month_2015_2024_stk_SEA.nc`

## Dataset summary

This dataset is a high-resolution monthly XCO2 product reconstructed using a background-constrained local spatiotemporal kriging (STK) method with CAMS background fields.

## Dimensions and coordinates

### `time`
- Type: `datetime64[ns]`
- Size: 120
- Description: monthly timestamps from January 2015 to December 2024

### `lat`
- Type: `float64`
- Size: 491
- Unit: degrees north
- Range: -16.0 to 33.0
- Description: latitude values on a 0.1° grid

### `lon`
- Type: `float64`
- Size: 611
- Unit: degrees east
- Range: 87.0 to 148.0
- Description: longitude values on a 0.1° grid

## Data variable

### `xco2`
- Type: `float32`
- Dimensions: `(time, lat, lon)`
- Unit: ppm
- Description: reconstructed monthly column-averaged dry-air mole fraction of atmospheric carbon dioxide

## Spatial and temporal coverage

- **Longitude**: 87.0°E to 148.0°E
- **Latitude**: 16.0°S to 33.0°N
- **Time range**: January 2015 to December 2024
- **Spatial resolution**: 0.1° × 0.1°
- **Temporal resolution**: monthly

## Global attributes

### `description`
High-resolution XCO2 reconstructed using STK and CAMS background fields.

### `creation_date`
Dataset creation time recorded in the NetCDF metadata.

## Notes

- The dataset is stored in NetCDF format.
- The main variable in the current version is `xco2`.
- Coordinate names are `time`, `lat`, and `lon`.
- Users should refer to the NetCDF metadata and repository documentation when using the dataset.
