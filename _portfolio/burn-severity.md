---
title: "Predicting Wildfire Burn Severity from Sentinel-2 Imagery and Field Observations"
excerpt: "Predicting Field-Measured Burn Severity for the 2016 Fuller Fire Using Sentinel-2 and Machine Learning.<br/><img src='/images/burn-severity/wildfire.jpg' width='518' height='346'>"
collection: portfolio
order: 3
---

## Project Overview
This project explores whether satellite observations and a simple machine-learning model can be used to predict field-measured wildfire burn severity. The analysis focuses on the 2016 Fuller Fire in northern Arizona, using pre- and post-fire Sentinel-2 imagery alongside field observations of the Composite Burn Index (CBI).

CBI provides a field-based measure of ecological fire effects ranging from 0 to 3, from little or no observable effect to high burn severity. Rather than using an existing satellite-derived burn-severity map as the modeling target, this project uses georeferenced CBI observations as an independent reference dataset.

Spectral information derived from Sentinel-2 imagery was extracted at CBI plot locations and used to train a simple decision-tree regression model. Model performance was compared with a baseline linear model using differenced Normalized Burn Ratio (dNBR), a commonly used spectral measure of wildfire effects.

## Objectives

### The primary objectives of this project are to:
Process and compare pre- and post-fire Sentinel-2 imagery for the 2016 Fuller Fire.
Calculate spectral indicators of vegetation condition and fire-related change, including NDVI and dNBR.
Integrate satellite observations with field-measured Composite Burn Index observations.
Train an interpretable decision-tree regression model to predict CBI from Sentinel-2 spectral characteristics.
Compare the multi-feature model with a simpler dNBR-only baseline.
Map predicted burn severity across the Fuller Fire perimeter and evaluate the strengths and limitations of the approach.

## Methods

### 1. Study Area and Reference Data

The 2016 Fuller Fire in northern Arizona was selected because of the availability of georeferenced field measurements spanning a broad range of burn severities. The fire perimeter was obtained from the Monitoring Trends in Burn Severity (MTBS) program, while field reference observations were obtained from the USGS Composite Burn Index dataset.

The national CBI dataset contained 99 observations for the Fuller Fire, with CBI values ranging from 0 to 2.93.

### 2. Sentinel-2 Image Selection

Pre- and post-fire Sentinel-2 imagery was identified using the Microsoft Planetary Computer STAC catalog. Candidate scenes were evaluated based on acquisition date, spatial coverage, and cloud contamination.

A June 12, 2016 acquisition was selected to represent pre-fire conditions. A November 9, 2016 acquisition was selected for post-fire conditions because it provided complete coverage of the study area with minimal cloud contamination.

Bands representing red (B04), near-infrared (B08), and shortwave infrared wavelengths (B11 and B12) were acquired along with the Sentinel-2 Scene Classification Layer (SCL).

### 3. Image Preprocessing

Sentinel-2 scenes intersecting the study area were mosaicked and aligned to a common 20-meter analysis grid. Higher-resolution bands were resampled to match the reference grid, and the SCL was used to identify invalid observations such as clouds and cloud shadows.

Pre- and post-fire imagery was then clipped to the Fuller Fire perimeter to create a consistent spatial dataset for subsequent analysis.

### 4. Spectral Change Analysis

Normalized Difference Vegetation Index (NDVI) and Normalized Burn Ratio (NBR) were calculated from the aligned Sentinel-2 imagery.

Changes between pre- and post-fire observations were represented using change in NDVI and differenced NBR (dNBR). These variables capture changes in vegetation condition and spectral response associated with wildfire effects.

### 5. Integration with Field CBI

Sentinel-2 predictor values were extracted at the locations of the field CBI observations. After excluding observations affected by invalid or missing imagery, 94 of the original 99 CBI plots remained available for modeling.

The resulting dataset paired each field-measured CBI value with spectral characteristics including pre- and post-fire SWIR reflectance, NDVI, vegetation change, and dNBR.

### 6. Baseline Burn-Severity Model

A simple linear regression between dNBR and field CBI was established as a baseline against which to evaluate the machine-learning model.

The baseline model achieved an R² of 0.343, with a mean absolute error (MAE) of 0.743 and root mean squared error (RMSE) of 0.876 on the held-out test observations.

### 7. Decision-Tree Regression

A shallow decision-tree regression model was trained using multiple Sentinel-2 predictors. Of the 94 usable observations, 75 were used for training and 19 for testing.

Model complexity was intentionally limited to maintain interpretability and reduce the risk of overfitting the relatively small field dataset.

The decision tree achieved an R² of 0.657, an MAE of 0.525, and an RMSE of 0.633 on the test set, outperforming the dNBR-only baseline.

### 8. Spatial Prediction

The trained model was applied to valid Sentinel-2 pixels throughout the Fuller Fire perimeter to produce a continuous predicted CBI surface ranging from 0 to 3.

The resulting map illustrates spatial variation in predicted ecological fire effects while also demonstrating how field observations can be combined with Earth observation imagery to extend measurements across a larger landscape.

## Results
The analysis found a positive but variable relationship between Sentinel-2 dNBR and field-measured CBI. The dNBR-only linear model explained approximately 34% of the variation in held-out CBI observations, indicating that dNBR captured meaningful burn-severity information but did not fully represent variation observed in the field.

The multi-feature decision tree produced stronger test-set performance, increasing R² from 0.343 to 0.657 while reducing MAE from 0.743 to 0.525. Post-fire NDVI was the most influential predictor in the fitted tree, followed by dNBR, post-fire B11 reflectance, and change in NDVI.

These results suggest that combining information about post-fire vegetation condition with spectral change metrics can provide additional information for predicting field-observed fire effects beyond a simple linear dNBR relationship.

![observed_vs_predicted_cbi](/images/burn-severity/observed_vs_predicted_cbi.png)
![decision_tree_feature_importance](/images/burn-severity/decision_tree_feature_importance.png)
![predicted_cbi_map](/images/burn-severity/predicted_cbi_map.png)

## Conclusion
This project demonstrates a workflow for integrating field observations with multispectral satellite imagery to model wildfire burn severity. Sentinel-2 spectral change showed a measurable relationship with field CBI, while a simple decision-tree model using multiple spectral predictors performed better on the held-out observations than a linear dNBR baseline.

The analysis also highlights several limitations. The dataset contained fewer than 100 usable field observations, model evaluation was based on a relatively small test set, and the 20-meter Sentinel-2 pixels do not perfectly correspond to the approximately 30-meter field CBI plots. Differences between the timing of satellite observations and field measurements may also influence the observed relationships.

Because the model was developed for a single fire, its predictions should not be interpreted as a general burn-severity model for other landscapes. Instead, the project demonstrates how remote sensing, field data, spectral change detection, and interpretable machine learning can be combined within a reproducible geospatial workflow.

### Repository
[View Code](https://github.com/jb-geo/burn-severity/blob/main/notebooks/analysis.ipynb)
