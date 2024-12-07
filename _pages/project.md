---
layout: research
title: "Research"
permalink: /research/
---

## Simulating the Annual Cycle of Antarctic Sea Ice

This work explores machine learning models to predict Antarctic sea ice extent, with a focus on forecasting its minimum extents. [Access the data and code here.]
***

## Introduction 
Sea ice plays a pivotal role in the Earth's climate system. It reflects the majority of incoming solar radiation, contributing to the maintenance of the equator-to-pole temperature gradient and mitigating global warming. Additionally, sea ice insulates the relatively warmer ocean from the frigid atmosphere, acting as a thermal barrier that regulates heat exchange between these two systems. It also serves as a protective shield for coastal glaciers, buffering them from ocean-driven melting. Changes in sea ice extent and thickness can disrupt thermohaline circulation, a critical component of the global ocean conveyor belt that drives climate patterns and influences oceanic heat distribution.

In recent years, Antarctic sea ice extent has reached unprecedented record lows, underscoring the urgency of improving our ability to predict its future behavior. The past three years of record-breaking minimum extents highlight the critical need for accurate projections of sea ice dynamics. Despite advances in modeling, current approaches, such as those employed in the Coupled Model Inter-comparison Project Phase 6 (CMIP6), face significant limitations. Many models misrepresent the timing of sea ice advance and retreat or fail to simulate realistic seasonal minimum and maximum extents. Although these models broadly predict sea ice decline by the end of the 21st century, the rate of loss remains uncertain due to substantial inter-model variability. This variability reduces confidence in the projections, especially when considering the dynamic and nonlinear processes governing sea ice behavior.

Predicting sea ice extent is inherently complex due to the interplay between atmospheric and oceanic processes. Physics-based models (like the CMIP models) rely thousands of lines of code to simulate these processes. However, they are often limited by uncertainties in climate forcing (e.g., global warming) or inaccuracies in representing key mechanisms such as ice-atmosphere and ice-ocean interactions. These limitations can lead to overestimation or underestimation of critical climate impacts. Accurate predictions are crucial for understanding the far-reaching implications of sea ice decline on the global climate system. 

This study explores the potential of machine learning (ML) to enhance predictions of Antarctic sea ice extent. Machine learning offers a more computationally efficient alternative to traditional physics-based models, leveraging large datasets to uncover patterns, trends, and possibly forecast. By utilizing daily sea ice extent data, this work aims to develop predictive models with improved accuracy. Sea ice extent, defined as the total area covered by at least 15% sea ice concentration within a pixel, serves as the target variable in this supervised regression framework.

To capture the multifaceted drivers of sea ice variability, the study incorporates sea surface temperature (SST), which directly impacts freezing and melting dynamics at the ocean-atmosphere boundary. Cooler SSTs promote freezing, while warmer SSTs lead to melting, with anomalously high SSTs potentially accelerating ice loss or delaying freezing [Thomas, Purich]. Surface pressure is also included as a proxy for wind patterns, which influence both dynamic processes such as ice transport and thermodynamic mechanisms like melt and freeze. These variations, often linked to different climate modes in the Southern Ocean (Southern Annular Mode, Zonal Wave 3, Semi-Annual, Southern Ocean, and Inter-decadal Oscillation) and ,  significantly impact regional sea ice extent [Raphael and Hobbs, 2014]. Lastly, latent and sensible heat fluxes are incorporated to represent energy exchanges at the ocean-atmosphere interface. Latent heat flux reflects the energy required for phase changes (e.g., ice melting or freezing), while sensible heat flux corresponds to the direct transfer of heat between air and sea, both of which regulate the rate of freeze and melt [Martinson].

By integrating these variables into machine learning models, this study seeks to advance our understanding of Antarctic sea ice dynamics and improve our ability to predict its extent. These models aim to bridge gaps in traditional approaches, offering a tool that can adapt to the inherent complexity and variability of the sea ice system. Ultimately, this work contributes to the broader goal of understanding how Antarctic sea ice responds to a changing climate and its implications for the global climate system.


This work aims to address the following questions:
- What features and factors are most influential in predicting sea ice?
- What model best captures Antarctic sea ice variability? 
- What is the predictive accuracy of machine learning models?


## Data
The dataset used in this project contains daily sea ice extent (SIE) measurements from 1979 to 2023. It was obtained from the National Snow and Ice Data Center (NSIDC). The primary features include `Day_of_Year` (1–365 or 366 for leap years), `Year`, `sin_day`, `cos_day`, and `Month`. The target variable is `Extent`, representing the SIE in 10⁶ km². We also incorporate daily ERA5 reanalysis data from the European Centre of Medium-Range Weather Forecasts (ECMWF). Satellite observations for sea ice go back to 1979-present day; therefore, the reanalysis data will serve the same timeframe. 

Reanalysis data are a mix of observations and previous short-range weather forecasts rerun with modern weather forecasting models. From the ERA5 Reanalysis we use 5 different variables: sea surface temperature (`sst`) , air surface temperature  (`t`), surface pressure  (`sp`), and latent (`mslhf`) and sensible heat (`msshf`) fluxes. All datasets were originally NetCDF gridded data from -50°S to 90°S. To facilitate the computational process, they have been spatially averaged for each day, taken the value at mid-day (12:00), and converted into a data frame.

| **Variable Name**                   | **Type**  | **Description**                                                                                   | **Units** | **Spatial Resolution** | **Temporal Resolution**          |
|-------------------------------------|-----------|---------------------------------------------------------------------------------------------------|-----------|------------------------|----------------------------------|
| **Mean Surface Latent Heat Flux**   | Numerical | The energy flux due to evaporation and condensation at the Earth's surface.                       | W/m²      | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Mean Surface Sensible Heat Flux** | Numerical | The heat exchange due to temperature differences between the surface and the atmosphere.          | W/m²      | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Sea Surface Temperature **        | Numerical | The temperature of the sea surface.                                                               | °K        | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Temperature at 850 hPa**          | Numerical | Atmospheric temperature at the 850 hPa pressure level.                                            | °K        | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Surface Pressure**                | Numerical | Atmospheric pressure at the Earth's surface.                                                      | Pa        | 0.25° x 0.25° (~28 km) | Hourly                           |
| **Sea Ice Extent**                  | Numerical | Sea ice concentration derived from satellite microwave radiometers using the Bootstrap Algorithm. | 10⁶ km²   | 25 x 25 km             | Daily (every other day pre-1987) |

![](assets/IMG/datapenguin.png){: width="500" }

*Figure 1: Here is a caption for my diagram. This one shows a penguin [1].*

## Modelling

### Feature Engineering
Feature engineering provides an easy way to enhance model performance and make the process a lot more interpretable using existing variables. For this work we take the day of year (DOY) and produce cyclical features to better represent the seasonality and continuity of the annual cycle of SIE. 

To do so we take the sine and cosine of each day: 

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

