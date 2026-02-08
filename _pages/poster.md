---
title: "Sub-seasonal Antarctic Sea Ice Phase Variability and Atmospheric Drivers"
layout: single
permalink: /poster/
author_profile: false
header:
  overlay: false
---

**Conference:** Climate and Cryosphere Open Science, 2026  
**Author:** Frida A. Perez

---
## Abstract
Antarctic sea ice exhibits pronounced variability on daily timescales, particularly near the ice edge and during periods of seasonal advance and retreat. While such variability is often treated as high-frequency noise around a fixed climatological seasonal cycle, growing evidence suggests that persistent daily fluctuations can accumulate and influence the timing and strength of the seasonal ice cycle itself. Here, we examine daily Antarctic sea ice extent (SIE) variability relative to an evolving seasonal reference that explicitly accounts for interannual shifts in seasonal phase and amplitude. Using an amplitude–phase adjusted annual cycle (APAC) framework, we separate smooth seasonal modulation from instantaneous daily departures, allowing daily variability to be characterized in terms of its magnitude, persistence, asymmetry, and timing within the seasonal cycle. We apply this framework across Antarctic sectors and seasons and assess how patterns of daily variability relate to large-scale atmospheric circulation. This approach clarifies when and where daily variability is most relevant for seasonal outcomes and provides a physically interpretable link between synoptic atmospheric forcing and seasonal-scale sea ice evolution.
## Extended Figures
### Reference Frames
This section demonstrates why the definition of the seasonal cycle fundamentally shapes how daily variability is interpreted.

Figures compare observed Antarctic SIE with three alternative seasonal references:

a traditional fixed climatology (TAC),

an invariant annual cycle (IAC), and

an amplitude–phase adjusted annual cycle (APAC).

The traditional climatological reference is fixed in both timing and magnitude and therefore misaligns with observed interannual shifts in advance, retreat, and seasonal strength. The invariant annual cycle captures the mean seasonal shape but cannot represent year-to-year changes in timing or amplitude. In contrast, APAC realigns the seasonal cycle to observed timing and magnitude while preserving a smooth seasonal backbone. As a result, phase shifts and smooth seasonal modulation are embedded within the seasonal reference rather than projecting onto daily anomalies.
### Seasonal Structure of Persistence
Using APAC-defined daily departures, we quantify variability in terms of:

magnitude (variance),

persistence (autocorrelation and run-length statistics),

asymmetry between positive and negative departures, and

timing relative to seasonal phase.

Results show that daily variability is not uniformly distributed throughout the year. Variability tends to be larger and more persistent during periods of seasonal advance and retreat, when the ice edge is highly mobile and the system is most sensitive to perturbations. In contrast, mid-winter and mid-summer plateaus are characterized by weaker persistence and reduced variability, consistent with stronger thermodynamic and dynamic constraints.
### Atmosphere-Sea Ice Coupling
We identify periods of persistent positive and negative daily departures (defined relative to APAC) and composite atmospheric conditions during these events using ERA5 fields. These composites reveal coherent circulation anomalies—such as persistent wind patterns and pressure anomalies—that differ by sector and season. The results suggest that when atmospheric forcing is sustained and aligned with seasonal sensitivity, daily variability can accumulate and contribute to shifts in seasonal timing or strength.

Importantly, by defining persistence after removing smooth seasonal modulation, this analysis avoids conflating atmospheric drivers of true sub-seasonal variability with those associated with seasonal phase shifts.
### Discussion
Together, these results highlight the importance of distinguishing between instantaneous daily variability and accumulated seasonal adjustment. Daily forcing acts continuously on the sea ice cover, but only a subset of that forcing—persistent, coherent, and seasonally aligned—accumulates into changes in seasonal phase or amplitude. The APAC framework separates these accumulated outcomes from transient daily departures, enabling both to be examined without conflation.
This perspective reframes daily variability not as noise, but as a process whose relevance depends on persistence and seasonal context. It also provides a framework for assessing whether changes in daily variability over recent decades reflect shifts in atmospheric forcing, sea ice sensitivity, or the efficiency with which the system integrates short-term perturbations.
---

## Methods Details

APAC and Daily Variability Framework

The amplitude–phase adjusted annual cycle defines an evolving seasonal reference whose timing and magnitude are allowed to vary from year to year. Daily variability is defined as departures from this evolving seasonal state, ensuring that smooth seasonal modulation and interannual phase shifts do not alias into daily anomaly signals.

Threshold Selection

Daily variability metrics are computed using concentration and extent thresholds consistent with community standards. Sensitivity tests demonstrate that the main results are robust to reasonable threshold choices.

Sector Definitions

Analyses are conducted for the full Antarctic domain and for standard Antarctic sectors (e.g., Weddell Sea, Ross Sea, Amundsen–Bellingshausen, East Antarctica, King Haakon), allowing regional contrasts in seasonal structure and atmospheric coupling.


---

## Code & Data

- **GitHub repository:**  
  https://github.com/falejandraperez/

- **Data sources:**  
  Bootstrap SMMR/SSMI, AMSR-E, ERA5

---
## Citations
1. Stammerjohn, S. E., Martinson, D. G., Smith, R. C., Yuan, X., and Rind, D.: Trends in Antarctic annual sea ice retreat and advance and their relation to El Niño–Southern Oscillation and Southern Annular Mode variability, J. Geophys. Res.-Oceans, 113,  C03S90, https://doi.org/10.1029/2007JC004269, 2008. 
2. Schlosser, E., Haumann, F. A., and Raphael, M. N.: Atmospheric influences on the anomalous 2016 Antarctic sea ice decay, The Cryosphere, 12, 1103–1119, https://doi.org/10.5194/tc-12-1103-2018, 2018.
3. Handcock, M. S. and Raphael, M. N.: Modeling the annual cycle of daily Antarctic sea ice extent, The Cryosphere, 14, 2159–2172, https://doi.org/10.5194/tc-14-2159-2020, 2020.
4. Himmich, K., Vancoppenolle, M., Madec, G. et al. Drivers of Antarctic sea ice advance. Nat Commun 14, 6219 (2023). https://doi.org/10.1038/s41467-023-41962-8
5.  Marshall, G. J. (2003). Trends in the Southern Annular Mode from Observations and Reanalyses. Journal of Climate, 16(24), 4134-4143. https://doi.org/10.1175/1520-0442(2003)016<4134:TITSAM>2.0.CO;2

---
## Contact

Email: falejandraperez@ucla.edu
