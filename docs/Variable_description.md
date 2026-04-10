# Variable description

This document describes the main dimensions, coordinates, variables, and metadata of the reconstructed XCO2 dataset provided in this repository.

## Dataset file

Main dataset file:

- `output/oco2_xco2_month_2015_2024_stk_SEA.nc`

## Dataset summary

This dataset is a high-resolution reconstructed monthly XCO2 product generated using a background-constrained local spatiotemporal kriging (STK) method with CAMS background fields.

## Dimensions

### `time`
Monthly time dimension of the dataset.

- Type: `datetime64[ns]`
- Size: 120
- Description: monthly timestamps of the reconstructed XCO2 fields from January 2015 to December 2024

### `lat`
Latitude dimension of the dataset.

- Type: `float64`
- Size: 491
- Unit: degrees north
- Range: -16.0 to 33.0
- Description: latitude coordinates of the regular grid

### `lon`
Longitude dimension of the dataset.

- Type: `float64`
- Size: 611
- Unit: degrees east
- Range: 87.0 to 148.0
- Description: longitude coordinates of the regular grid

## Coordinates

### `time`
- Coordinate type: temporal coordinate
- Description: monthly time stamps from January 2015 to December 2024

### `lat`
- Coordinate type: spatial coordinate
- Description: latitude values on a 0.1° grid

### `lon`
- Coordinate type: spatial coordinate
- Description: longitude values on a 0.1° grid

## Data variable

### `xco2`
Column-averaged dry-air mole fraction of atmospheric carbon dioxide.

- Dimensions: `(time, lat, lon)`
- Type: `float32`
- Unit: ppm
- Description: reconstructed monthly XCO2 field generated using STK with CAMS background constraints

## Temporal coverage

- Start time: 2015-01-01
- End time: 2024-12-01
- Temporal resolution: monthly

## Spatial coverage

- Longitude range: 87.0°E to 148.0°E
- Latitude range: 16.0°S to 33.0°N
- Spatial resolution: 0.1° × 0.1°

## Global attributes

### `description`
High-resolution XCO2 reconstructed using STK and CAMS background fields.

### `creation_date`
Dataset creation time recorded in the NetCDF file metadata.

- Value in current file: `2026-03-29 06:56:42`

## Notes

- The dataset is stored in NetCDF format.
- The main variable in the current version is `xco2`.
- Coordinate names are `time`, `lat`, and `lon`.
- Users should refer to the file metadata and repository documentation when using later versions of the dataset, as metadata entries may be updated in future releases.
