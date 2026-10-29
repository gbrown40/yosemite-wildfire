# Yosemite Wildfire Susceptibility Mapping

## Overview

This project uses geospatial analysis and machine learning to examine historical wildfire patterns in Yosemite National Park, California. It investigates how different spatial train/test splitting strategies affect the evaluation of models estimating **historical burn susceptibility**.

**Research question:** How does spatial train/test methodology affect the evaluation of wildfire susceptibility models in Yosemite National Park?

## Data Sources

* **CAL FIRE:** Historical wildfire perimeters
* **USGS 3DEP:** Elevation data used to derive elevation, slope, and aspect
* **NLCD:** Land cover classifications
* **OpenStreetMap:** Roads, trails, and campsites
* **National Park Service:** Park boundaries

## Methodology

A 500 m × 500 m grid was created across the study area. Each cell was labeled as burned or unburned based on its intersection with historical fire perimeters. Terrain, land cover, and infrastructure-related features were used as model predictors.

Two classification models were evaluated:

* **Logistic Regression**
* **Random Forest**

Four train/test strategies were compared:

1. Random stratified split
2. Spatial-block split
3. Geographic holdout (western training region, eastern testing region)
4. Buffered geographic holdout, excluding observations within 5 km of either side of the geographic boundary

Model performance was assessed using balanced accuracy, average precision, F1-score, precision, and recall.

## Tools

Python, GeoPandas, Pandas, NumPy, scikit-learn, GDAL, QGIS, and Matplotlib.

## Key Findings

Model performance varied across validation strategies, highlighting the importance of spatial separation when evaluating environmental machine learning models. Random splits may provide overly optimistic estimates of geographic generalization when nearby observations occur in both training and testing sets.

## Limitations

The model identifies patterns associated with historical burn occurrence; it does not predict future wildfires or represent a complete wildfire risk assessment. Results are also influenced by the resolution of the analysis grid, historical fire data, and the choice of spatial validation strategy.

## Reproducibility

Download the datasets listed above, install the required Python packages, and run the analysis notebook in sequence. Update file paths as needed for your local environment.

*An environmental data science portfolio project exploring geospatial analysis, machine learning, and spatial validation.*
