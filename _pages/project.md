---
layout: research
title: "Research"
permalink: /research/
---


## Predicting Antarctic Sea Ice Minima

This paper examines different machine learning models for the best prediction of Antarctic sea ice minima. Please find the data and code using the following links: 
Data -
Code -
***

## Introduction 

The last three years have consisted of record lows for sea ice extent in the Southern Ocean. Antarctic sea ice predictions are notorious for having a large intermodel spread in the climate Coupled Model Intercomparison Projects.The latest phase, CMIP6 showed significant improvements in different areas, but the models were unable to capture mean states of the annual cycle. Either the timing of sea ice advance or retreat begins a lot later than the observed or simulate different maximum and minimum extents. For example, they underestimate the summer minimum and although most models predict sea ice loss by the 21st century, confidence in the rate of loss is limited. These models are based on physics, with thousands of line of code simulating different components of the sea ice interface. Sea ice is incredibly hard to model, because it is affected by the atmosphere above and the ocean below. It is possible that models are exagerating the climate forcing (global warming) or that there existing flaws in the physics, i.e the representation of sea ice processes. Sea ice reflects 70% of the incoming solar radiation, it insulates the ocean from the atmosphere, protects glaciers, and helps form the thermohaline circulation- maintaining the equator-pole temperature gradient. It is important we are able to predict sea ice, since it plays a huge role in the climate system. 

Machine learning allows us to explore sea ice variations and predict future scenarios. This is a different approach to the problem, and is much less computationally expensive. This work attempts to capture the annual cycle of Antarctic sea ice, as well as predict future sea ice minimum extent values using different statistical models. Sea ice extent is a measures of sea ice, it is the total region with at least 15 percent sea ice cover. NSIDC usually reports extent, which gives higher values than area.
Our target variable is sea ice extent, and because we are trying to predict and capture a specific value, we consider this a supervised classification problem. 

The guiding questions of this project are: 
 - What factors influence sea ice extent?
 - Can we predict sea ice minima?
 - How accurate is a model in simulating sea ice extent? What about predicting its minima? 
 
This work will be using satellite data from the National Snow and Ice Data Center (NSIDC) for sea ice extent from 1979-2023 along with reanalysis data from the ERA5 project. 

## Data
The dataset used in this project contains daily sea ice extent (SIE) measurements from 1979 to 2023. It was obtained from the National Snow and Ice Data Center (NSIDC). The primary features include Day_of_Year (1–365 or 366 for leap years), Year, sin_day, cos_day, and Month. The target variable is Extent, representing the sea ice extent in 10⁶ km².
Here is an overview of the dataset, how it was obtained and the preprocessing steps taken, with some plots!
- sea surface temperature, total precipitation, air surface temperature, subsurface temperature, latent and sensible heat, wind speed, surface pressure, and specific humidity. 

![](assets/IMG/datapenguin.png){: width="500" }

*Figure 1: Here is a caption for my diagram. This one shows a pengiun [1].*

## Modelling
Explain data preparation and feature engineering (e.g., sin_day, cos_day).
Describe each model and why it was chosen.

Here are some more details about the machine learning approach, and why this was deemed appropriate for the dataset. 

The model might involve optimizing some quantity. You can include snippets of code if it is helpful to explain things.

```python
from sklearn.ensemble import ExtraTreesClassifier
from sklearn.datasets import make_classification
X, y = make_classification(n_features=4, random_state=0)
clf = ExtraTreesClassifier(n_estimators=100, random_state=0)
clf.fit(X, y)
clf.predict([[0, 0, 0, 0]])
```

This is how the method was developed.

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

