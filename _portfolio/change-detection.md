---
title: "Detecting Vegetation Change Around the Port of Savannah (2016-2024)"
excerpt: "Evaluate changes in vegetation surrounding the Port of Savannah using multi-temporal Sentinel-2 imagery and NDVI. <br/><img src='/images/change-detection/pexels-attie-9296993.jpg' width='518' height='346'>"
collection: portfolio
order: 2
---

## Project Overview
This project applies open-source remote sensing and geospatial analysis techniques to assess infrastructure expansion in the Port of Savannah region between 2015 and 2024. The analysis simulates a GEOINT-style workflow focused on identifying, quantifying, and interpreting land use change related to logistics and port operations.

## Objectives

### The primary objectives of this project are to:

- Process multi-temporal Sentinel-2 Level-2A imagery using Python
- Apply a study-area boundary using a GeoJSON file
- Mask clouds and other invalid pixels using the Sentinel-2 Scene Classification Layer (SCL)
- Prepare consistent imagery for comparison across multiple years
- Calculate Normalized Difference Vegetation Index (NDVI)
- Examine changes in vegetation and land cover across the study period
- Create clear visual outputs that demonstrate the results of the analysis

## Methods

The analysis is organized into a series of preprocessing and analysis steps.

### 1. Project Configuration

The notebook defines the project directory, input imagery locations, study-area boundary, output directories, image years, and Sentinel-2 bands.

pathlib.Path is used to manage file paths.

### 2. Study Area Preparation

The study-area GeoJSON is loaded using GeoPandas.

The boundary is used to define the area of interest for the raster processing workflow.

### 3. Sentinel-2 Band Identification

The Sentinel-2 .SAFE directories contain imagery organized into nested folders. A helper function recursively searches the directories to locate the required .jp2 files for each band.

### 4. Cloud and Invalid Pixel Masking

The Sentinel-2 Scene Classification Layer is used to identify pixels that should be excluded from the analysis.

Masked pixels are assigned NaN values so that they are ignored during subsequent calculations.

### 5. Raster Clipping

The Sentinel-2 bands are clipped to the study-area boundary using Rasterio.

The resulting GeoTIFF files are stored in the project outputs directory.

### 6. NDVI Calculation

NDVI is calculated using the red and near-infrared bands:

NDVI= (NIR−Red)/(NIR+Red)
	​
NDVI provides a simple measure of vegetation activity and allows vegetation patterns to be compared across the study years.

### 7. Change Detection

NDVI outputs from different years are compared to identify areas where vegetation conditions changed over the study period.

The resulting difference imagery provides a spatial representation of vegetation change within the study area.

### 8. Visualization

RGB composites and NDVI-based figures are generated using Matplotlib.

The RGB composites provide visual context for interpreting the changes identified by the analysis.

## Results

### RGB Imagery
![RGB 2016](/images/change-detection/rgb_2016.png)
![RGB 2024](/images/change-detection/rgb_2024.png)

### NDVI
![Delta NDVI](/images/change-detection/delta_ndvi.png)

### Histogram
![Distribution of Vegetation Change](/images/change-detection/delta_histogram.png)

## Conclusion
This analysis used multi-temporal Sentinel-2 imagery to examine vegetation change around the Port of Savannah between 2016 and 2024. Mean NDVI declined from 0.288 in 2016 to 0.250 in 2024, while the overall mean ΔNDVI was -0.021. Across the valid pixels in the study area, 58.9% showed a decrease in NDVI compared with 41.1% showing an increase.

The spatial distribution of change shows that vegetation loss was concentrated in several developed and industrial areas, while increases in NDVI occurred in portions of the surrounding vegetated landscape. This demonstrates how multispectral imagery can be used to identify and visualize spatial patterns of landscape change that may not be apparent from aerial imagery alone.

Because the analysis compares three individual image dates rather than a continuous time series, some of the observed differences may reflect seasonal and environmental conditions in addition to actual land-cover change. The results should therefore be interpreted as an example of spatial vegetation change detection rather than a definitive measure of long-term vegetation loss.

### Repository
[View Code](https://github.com/jb-geo/savannah-port-change-detection/blob/main/notebooks/raster_analysis.ipynb)
