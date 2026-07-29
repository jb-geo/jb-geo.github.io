---
title: "Detecting Vegetation Change Around the Port of Savannah (2016-2024)"
excerpt: "Evaluate changes in vegetation surrounding the Port of Savannah using multi-temporal Sentinel-2 imagery and NDVI. <br/><img src='/images/change-detection/pexels-attie-9296993.jpg' width='518' height='346'>"
collection: portfolio
order: 2
---

## Project Overview

### Why NDVI?

NDVI measures vegetation vigor using the contrast between near-infrared reflectance and red reflectance.

Healthy vegetation strongly reflects NIR while absorbing red light, producing high NDVI values.

Comparing NDVI between years provides a simple yet effective indicator of vegetation gain or loss associated with urban expansion.

### Research Question
How has vegetation changed around the Port of Savannah between 2016 and 2024, and can these changes be quantified using automated remote sensing techniques?

## Data
| Dataset                    | Purpose               |
| -------------------------- | --------------------- |
| Sentinel-2 Level-2A        | Multispectral imagery |
| Band 4                     | Red                   |
| Band 8A                    | Near Infrared         |
| Scene Classification Layer | Cloud masking         |
| Study Area Polygon         | Clip boundary         |

### Workflow
Sentinel-2 SAFE

↓

Extract spectral bands

↓

Cloud / shadow masking

↓

Clip to AOI

↓

Calculate NDVI

↓

Calculate ΔNDVI

↓

Visualize vegetation change

↓

Interpret results
### Results

#### RGB Imagery

Three images showing

2016

↓

2020

↓

2024

NDVI

Three maps

2016

↓

2020

↓

2024

#### ΔNDVI

One large figure

Use a diverging color ramp

Red = vegetation loss

Green = vegetation gain

#### Histogram

### Discussion

### Repository

[View Code](https://github.com/jb-geo/savannah-port-change-detection/blob/main/notebooks/raster_analysis.ipynb)
