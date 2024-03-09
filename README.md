# PlantTraits2024 - FGVC11 Kaggle Competition

This repository contains my code submissions for the Kaggle competition [PlantTraits2024 - FGVC11](https://www.kaggle.com/competitions/planttraits2024).

## Overview
The goal is to predict a broad set of 6 plant traits (e.g. leaf area, plant height) from crowd-sourced plant images and some ancillary data.


## Dataset

The dataset provided for this competition includes images of various plant species along with associated tabular values. To create this database, the organizers utilized the TRY database (trait information) and the iNaturalist database (citizen science plant photographs). 

Based on the species names found in both databases, the trait observations obtained from the TRY database (species-specific mean and standard deviation) were linked with the plant photographs from iNaturalist. Additionally, using the geocoordinates associated with each plant photograph, ancillary predictors were linked. These predictors are derived from globally available raster data including:

- **WORLDCLIM**: Includes temperature and precipitation data.
- **SOIL**: The global soil grids dataset, providing interpolated products on various soil properties such as sand content or pH value.
- **MODIS**: Satellite data that measures optical reflectance of sunlight, similar to a camera but with many wavelengths.
- **VOD**: Represents data from a radar constellation sensitive to water content and biomass of plants.

## Approach

- **v1**
    - Data Augmentation :
        - Resizing (`224x224`)
        - Normalizing
    - Model trained on a sample of data (5000 instances)
    - Model Overview :
        - CNN Backbone - `efficientnet_b0`
        - For tabular values - `Linear`
        - Combined output - `Linear`
    - Optimizer - `Adam`, with no learning rate scheculer (LR = `1e-4`)
    - `X[*]_sd` columns not used for training