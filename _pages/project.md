---
layout: research
title: "Research"
permalink: /research/
---

## Simulating the Annual Cycle of Antarctic Sea Ice

This work explores machine learning models to predict Antarctic sea ice extent, with a focus on forecasting its minimum extents. [Access the data and code here.]

---

## Introduction

Sea ice plays a pivotal role in the Earth's climate system. It reflects most incoming solar radiation, contributing to the maintenance of the equator-to-pole temperature gradient and mitigating global warming. Additionally, sea ice insulates the relatively warmer ocean from the frigid atmosphere, acting as a thermal barrier that regulates heat exchange between these two systems. It also serves as a protective shield for coastal glaciers, buffering them from ocean-driven melting.

Changes in sea ice extent and thickness can disrupt thermohaline circulation, a critical component of the global ocean conveyor belt that drives climate patterns and influences oceanic heat distribution. Recent record lows in Antarctic sea ice extent underscore the urgency of improving predictive capabilities.

Despite advances in modeling, current approaches, such as CMIP6, face limitations. Models often misrepresent the timing of sea ice advance and retreat or fail to simulate realistic seasonal minimum and maximum extents. Machine learning offers a complementary approach by leveraging large datasets to uncover patterns and forecast future behavior more efficiently.

This study aims to answer:
- What features and factors are most influential in predicting sea ice?
- Which model best captures Antarctic sea ice variability?
- What is the predictive accuracy of machine learning models?

---

## Data

The dataset includes daily sea ice extent (SIE) measurements from 1979 to 2023 obtained from the NSIDC, alongside daily ERA5 reanalysis data from ECMWF. Key features and target variables include:

| **Variable Name**                   | **Type**  | **Description**                                                                  | **Units** | **Spatial Resolution** | **Temporal Resolution**          |
|-------------------------------------|-----------|----------------------------------------------------------------------------------|-----------|------------------------|----------------------------------|
| **Mean Surface Latent Heat Flux**   | Numerical | Energy flux due to evaporation and condensation at the surface.                  | W/m²      | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Mean Surface Sensible Heat Flux** | Numerical | Heat exchange due to temperature differences between the surface and atmosphere. | W/m²      | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Sea Surface Temperature**         | Numerical | Temperature of the sea surface.                                                  | °K        | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Temperature at 850 hPa**          | Numerical | Atmospheric temperature at the 850 hPa pressure level.                           | °K        | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Surface Pressure**                | Numerical | Atmospheric pressure at the surface.                                             | Pa        | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Sea Ice Extent**                  | Numerical | Sea ice concentration derived from satellite microwave radiometers.              | 10⁶ km²   | 25 x 25 km             | Daily (every other day pre-1987) |

---

## Modelling

### Feature Engineering

To enhance interpretability and performance, cyclical features represent the annual cycle of SIE:

```python
import numpy as np
SIE_DF['sin_day'] = np.sin(2 * np.pi * SIE_DF['Day_of_Year'] / 365)
SIE_DF['cos_day'] = np.cos(2 * np.pi * SIE_DF['Day_of_Year'] / 365)

```

Another way to improve the performance of the model is to include lagged features. This is important because the climate system is not linear and the response of the ice to all forcings can occur at different timescales. The ocean has a longer memory, given waters high heat capacity, so effects might be seen in following seasons or even years. The atmosphere is a lot more ephemeral and its impacts can be seen at sub-monthly timescales.

The following lag and lead times are considered for each variable: 
- SIE :
  - 6 month lag: 2 seasons (180 days). 
  - 12 month lag: 1 year (365 days). 

- Sea Surface Temperature (SST):
  - 3 month lag: 1 season (90 days)
  - 12 month lag: 1 year (365 days). 

- Air Temperature:
  - 1 week lag: short-term (7 days). 
  - 1 month lag: med-term (30 days).

## Results

Figure X shows... [description of Figure X].

## Discussion

From Figure X, one can see that... [interpretation of Figure X].

## Conclusion

Here is a brief summary. From this work, the following conclusions can be made:
* first conclusion
* second conclusion

Here is how this work could be developed further in a future project.

## References
[1] DALL-E 3

[back](./)

