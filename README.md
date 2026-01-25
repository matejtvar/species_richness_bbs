# SDS_assignement
## Scale dependence and temporal stability of NDVI–species richness relationships in North American breeding birds

This is a code for the final assignement of Spatial Data Science for Social Geography course (see:https://martinfleischmann.net/sds/).

This project examines how spatial variation in vegetation productivity and geographic location predict observed bird species richness across the contiguous United States. Using Breeding Bird Survey data from 2018 aggregated to multiple equal-area grid resolutions, I apply Random Forest regression to assess scale-dependent relationships and spatial generalization. The analysis focuses on methodological challenges related to spatial aggregation, sampling bias, and non-linear modelling.

Area of interest: US

Temporal scope: 2018

Datasets used: 
- BBS (for species richness): number of unique bird species observed in each grid cell computed by aggregating BBS routes intersecting each cell
- Terra/MODIS (for NDVI)
- States boundaries

Grid size: H3 indexes resolutions 2, 3 and 4

Sampling controls and spatial predictors:
- latitude (cell centroid)
- longitude (cell centroid)
- mean elevation
- elevation sd
- n_routes
- routegrid_ratio

$\text{route coverage} = \frac{\text{total BBS route length inside grid cell (km)}}{\text{grid cell area (km}^2\text{)} }$

Spatial aggregation

- BBS routes intersected with equal-area grid cells
- Species richness computed as unique species per cell
- NDVI summarized as mean value per cell

Spatial autocorrelation

Modelling

- Random Forest regression fitted separately for each grid resolution: randomForest(richness ~ ndvi_mean + elev_mean + elev_sd + lat + lon + n_routes + routegrid_ratio)
- Model performance evaluated using cross-validation
- Residuals mapped to identify spatial structure
