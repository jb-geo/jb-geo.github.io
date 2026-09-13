---
title: "Monitoring Seasonal River Ice Dynamics Using Sentinel-1 SAR"
excerpt: "Using Sentinel-1 SAR imagery to investigate seasonal river ice dynamics at the Yukon-Tanana Confluence.<br/><img src='/images/river-ice/brigachtal-yukon-495348.jpg' width='518'>"
collection: portfolio
order: 1
author_profile: true

---

## Project Overview

This project explores the use of Sentinel-1 Synthetic Aperture Radar (SAR) imagery to monitor seasonal changes in river ice at the confluence of the Yukon and Tanana Rivers in interior Alaska. Because SAR can collect observations independent of daylight and cloud cover, it provides a useful tool for monitoring freeze-up and break-up in high-latitude environments where optical imagery can be limited.

### Research Question

How effectively can Sentinel-1 SAR imagery be used to identify and track seasonal changes in river ice coverage?

## Data
The analysis uses a time series of Sentinel-1 SAR imagery over the Yukon–Tanana confluence. VV-polarized radar backscatter was analyzed within a water-focused area of interest to examine changes in surface conditions through the freeze-up and break-up seasons.

### Methods
The workflow combined SAR image processing and temporal analysis to estimate changes in river ice coverage through time. Major steps included:

- filtering SAR imagery to reduce speckle
- examining distributions of VV backscatter
- applying a backscatter threshold to classify probable ice
- restricting analysis to a water-focused area of interest
- calculating the percentage of the analyzed area classified as ice for each observation
- comparing classification results through time to identify seasonal patterns

## Key Findings

The analysis identified a clear seasonal pattern in radar backscatter and estimated ice coverage. Within the defined area of interest, classified ice coverage reached approximately 35% during peak freeze conditions.

The time series also showed that freeze-up was not represented by a simple, continuous increase in classified ice. An initial increase was followed by a temporary decline before coverage increased again later in the winter, illustrating the dynamic nature of river-ice conditions and the value of repeated observations rather than single-date imagery.

## Interpretation and Limitations

The results demonstrate the potential of Sentinel-1 SAR for monitoring seasonal river-ice dynamics, particularly in regions where cloud cover and limited daylight can constrain optical remote sensing.

However, the analysis relies on a relatively simple backscatter-threshold classification. Radar backscatter can vary with surface roughness, snow conditions, ice structure, viewing geometry, and other environmental factors, meaning that threshold-based classifications should not be interpreted as direct measurements of ice extent without additional validation.

Future work could incorporate additional SAR polarizations, more advanced classification approaches, field or external validation data, and multi-year observations to better distinguish ice conditions and evaluate interannual variability.

### Results

![Time Series](/images/river-ice/ice_area_2024_2025.png)
While a clear seasonal trend in radar backscatter emerged across the study years, freeze-up was not continuous in nature. This is apparent in the temporary spikes in ice coverage throughout each winter season.
![VV Backscatter](/images/river-ice/histogram_jan_2023.png)

![Ice Classification](/images/river-ice/ice_classification_jan_2023.png)


### Repository

[View Code](https://github.com/jb-geo/ice-and-open-water-classification/blob/main/notebooks/ice_monitoring.ipynb)

## Full Technical Report

This project also includes a longer technical write-up
covering methodology, results, interpretation, and discussion.

[Read Full Report](/files/monitoring-seasonal-river-ice-dynamics.pdf)
