# This script converts an 8-bit NDVI raster (with NDVI values scaled for storage as integers) into a float32 raster, rescales the values to the standard NDVI range (-1 to 1), and computes
# a soil cover management C-factor raster for use in soil erosion models such as WaTEM/SEDEM. The output is a float32 GeoTIFF with C-factor values in the range [0, 1].
# NDVI to C-Factor Raster Conversion

This script converts an 8-bit NDVI raster (typically scaled and stored as integers for efficient storage) to a float32 raster, rescales the values to the standard NDVI range (-1 to 1), and computes a C-factor raster for soil erosion modeling (e.g., WaTEM/SEDEM).

## What It Does

- **Reads** a single-band NDVI raster (8-bit, e.g., values -75 to 61).
- **Rescales** integer NDVI values to real NDVI values (-1 to 1).
- **Computes** a C-factor raster using the formula:

where α is an empirical parameter (default α=2.0).
- **Saves** the result as a float32 GeoTIFF, suitable for WaTEM/SEDEM or other soil erosion models.

## Usage

1. Install dependencies:

 ```bash
 pip install rasterio numpy

ndvi_path = r"E:\DEMs\Headwaters_Boyer_River\8bit_NDVI.tif"
c_factor_path = r"E:\DEMs\Headwaters_Boyer_River\C_Factor_float32.tif"
