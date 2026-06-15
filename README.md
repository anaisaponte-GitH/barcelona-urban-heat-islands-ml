# Urban Heat Island Risk Prediction in Barcelona

## Overview

This project develops an end-to-end Machine Learning solution capable of identifying **Urban Heat Island (UHI) risk areas** in Barcelona using satellite imagery, environmental indicators, and geospatial data.

The objective was to determine whether it is possible to predict urban heat risk **without using temperature measurements as model inputs**, relying instead on spectral signatures extracted from publicly available satellite data.

🔗 **Live Demo:** https://uhi-risk-model.streamlit.app/

---

## Business Problem

Urban Heat Islands (UHI) are areas within cities that retain significantly more heat than their surrounding environment, particularly during the night.

This phenomenon is associated with:

* High building density
* Limited vegetation coverage
* Impermeable urban surfaces
* Reduced water presence

UHI affects public health, energy consumption, and overall quality of life in urban environments.

Traditional monitoring depends on temperature sensors with limited spatial coverage. This project explores whether satellite imagery can be used to identify high-risk areas at scale.

---

## Project Goal

Build a Machine Learning model capable of classifying urban locations into:

* **Risk** → Areas with elevated Urban Heat Island risk
* **No Risk** → Areas without significant thermal risk

The final solution was designed to support environmental monitoring, urban planning, and climate resilience initiatives.

---

## Dataset

The dataset was created by combining multiple geospatial data sources through Google Earth Engine.

### Dataset Characteristics

* **69,683 observations**
* **Barcelona metropolitan area**
* **Period:** 2020–2025
* **Multitemporal environmental data**
* **14 predictive variables**

The target variable (**uhi_risk**) was generated from nighttime thermal anomalies derived from MODIS surface temperature measurements.

---

## Data Sources

### Sentinel-2 (European Space Agency)

Provides spectral information used to generate environmental indicators such as:

* NDVI (Vegetation)
* NDBI (Built-up Areas)
* NDWI / MNDWI (Water Presence)
* NDMI (Moisture)
* NBR (Burned Areas)

### MODIS (NASA)

Provides:

* Daytime surface temperature
* Nighttime surface temperature

Used exclusively to construct the target variable.

### SRTM Elevation Data

Provides terrain elevation and topographic information.

### Google Earth Engine

Used as the cloud-based platform for satellite image acquisition, filtering, processing, and dataset generation.

---

## Exploratory Data Analysis

The EDA phase revealed clear relationships between environmental conditions and Urban Heat Island risk:

### Key Findings

* Lower NDVI values are associated with higher UHI risk.
* Higher urbanization indicators (NDBI) correlate with increased thermal risk.
* Nighttime thermal anomalies strongly differentiate Risk and No Risk areas.
* Terrain elevation influences heat distribution patterns.

These findings confirmed that satellite-derived variables contain predictive signals capable of identifying UHI-prone areas.

---

## Machine Learning Approach

Three supervised learning algorithms were evaluated:

| Model         | Accuracy | Recall (Risk) | F1 Score (Risk) |
| ------------- | -------- | ------------- | --------------- |
| XGBoost       | 0.72     | 0.75          | 0.74            |
| Random Forest | 0.71     | 0.73          | 0.72            |
| SVM           | 0.71     | 0.75          | 0.73            |

Additional experiments were performed removing geographic coordinates to evaluate model generalization capability.

| Final Selected Model                    | Accuracy | Recall | F1 Score |
| --------------------------------------- | -------- | ------ | -------- |
| XGBoost Optimized (Without Coordinates) | 0.68     | 0.73   | 0.71     |

---

## Why XGBoost Was Selected

Although several models achieved similar performance, XGBoost was selected because it offered the best balance between:

* Predictive performance
* Recall for high-risk areas
* Robustness
* Environmental generalization capability

The final version intentionally excludes geographic coordinates to reduce location dependency and improve transferability to other urban environments.

---

## Feature Importance

The most influential variables identified by the final model were:

1. Elevation
2. Summer seasonality
3. NDVI (Vegetation Index)
4. NIR and SWIR spectral bands
5. Water-related indices (MNDWI, NDWI)

These results align with known environmental factors associated with Urban Heat Island formation.

---

## Interactive Application

The project includes a Streamlit web application that allows users to:

* Explore model performance metrics
* Analyze feature importance
* Visualize geospatial predictions
* Navigate interactive heat-risk maps
* Generate individual predictions

### Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* XGBoost
* Streamlit
* Folium
* Google Earth Engine
* Remote Sensing
* Geospatial Analysis

---

## Results

The project demonstrates that Urban Heat Island risk can be predicted using publicly available satellite imagery and environmental indicators without requiring temperature measurements as model inputs.

The final model successfully captures environmental patterns associated with urban heat accumulation and provides actionable insights for city-scale analysis.

---

## Potential Applications

* Urban Planning
* Climate Resilience Programs
* Environmental Monitoring
* Green Infrastructure Prioritization
* Sustainability Initiatives
* Early Warning Systems

---

## Authors

Developed as the Final Project of the Data Science & Machine Learning Bootcamp at 4Geeks Academy.

**Team**

* Anais Aponte
* Balam Castro
* Cristina Cerverón

---

### About Me

This repository is part of my Machine Learning portfolio and reflects my interest in applying Data Science and Artificial Intelligence to real-world environmental and geospatial challenges.
