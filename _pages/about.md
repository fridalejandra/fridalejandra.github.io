---
permalink: /
title: "Hey!"
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% include base_path %}

My name is Frida, and I am currently a Ph.D. candidate in Geography at UCLA, specializing in polar climates and sea ice dynamics. My research broadly focuses on understanding the physical processes that govern sea ice variations and its role in climate systems. Using statistics and remote sensing, I explore the seasonal cycles of sea ice extent - the annual advance and retreat periods, to better predict future climate patterns.


[](/images/icy.JPEG){: .align-left width="100px"}


As a graduate student, part of my role involves teaching. Being a first-generation immigrant and student has often made academia feel unfamiliar, but despite the challenges, it has been incredibly rewarding. I never imagined taking this path, but through my coursework and the guidance of mentors, I have been inspired to stay curious, ask questions, and persevere. I am now dedicated to bridging the gap between scientific research and education. Through my work, I hope to inspire other students to also pursue research.

[](/images/nino_rock.jpg){: .align-right width="100px"}

When I’m not deep in research or perfecting my figures in Matplotlib, you can find me cooking, jamming, watching thrillers, or enjoying the outdoors—most likely at the beach. 

Antarctic Sea Ice Phase 
======
My current work focuses on the phase of Antarctic sea ice — the time it advances and retreats — using daily sea ice data from 2012 to 2023. The study investigates the relationship between sea ice seasonality and atmospheric circulation patterns, including the [Southern Annular Mode](https://www.antarcticglaciers.org/glaciers-and-climate/southern-annular-mode/), [Semi-Annual Oscillation](https://webspace.science.uu.nl/~broek112/home.php_files/Publications_MvdB/2000b_VanDenBroeke_IJC.pdf), and [Zonal Wave 3](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2004GL020365), to understand the drivers of sea ice variability. By examining external forces like solar radiation alongside internal atmospheric mechanisms, the research aims to provide more accurate estimates of sea ice phase. These findings will help clarify how Antarctic sea ice responds to the atmosphere (or vice versa), contributing to improved predictions of sea ice trends and their impact on the global climate system.

For example, when we look at the annual cycle of Antarctic sea ice averaged over space (bottom) the day when the ice begins to retreat (melt~September) and advance (freeze~February) appears coherent. 

[](/images/AGU_nsidc_sie_cpolar.png)

However, when we look at the timing of Advance (left) and Retreat (right), we can see that they are not homogenous over space nor time, especially timing of retreat. 
![Advanced Output GIF](/images/adv_output_white.gif) ![RTR Output GIF](/images/rtr_output_without.gif)



Sea Ice Thickness 
======
Sea ice thickness (SIT) has historically been difficult to measure due to the challenges of acquiring data at depth. However, starting in the early 2000s, estimates of SIT from satellites like CryoSat and Envisat became available. These polar-orbiting satellites use radar altimetry to measure the ice. A radar signal is sent from the satellite, and the time it takes to return is used to calculate the height of the ice above sea level, known as the freeboard (see image below).

[](/images/SIT_diagram.png)

* _Freeboard_: The height of the sea ice and snow layers above sea level.
* _Draft_: The part of the ice below sea level, which, when combined with the freeboard, allows us to estimate the total ice thickness.

By using the freeboard measurement and the known density of ice, the overall thickness of the sea ice can be calculated. This method is similar to how sea level is measured using radar altimetry—by determining the time it takes for the radar pulse to return, we can calculate the distance from the satellite to the surface and isolate the freeboard by subtracting the satellite's orbit.

[](/images/vol_output_white.gif)

Using satellite altimetry data from Envisat and CryoSat-2, I analyzed the spatial and temporal variation of SIT and sea ice volume (SIV) around Antarctica from 2003 to 2011.
* **Key Findings**: The thickest ice was found near the continent, with more variability along the sea ice edge. 

* **SIT and SIA Relationship**: By examining the relationship between sea ice area (SIA) and SIT, I discovered complex interactions, with positive and negative correlations across different regions. These insights are crucial for accurately estimating sea ice volume.

This work enhances our understanding of how Antarctic sea ice regulates energy exchange between the ocean and atmosphere, improving predictions of sea ice trends, which are critical for assessing the global climate system.