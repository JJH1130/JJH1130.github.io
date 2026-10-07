# Long-Term Climate Warming and Urban Heat Island Effect in Seoul, South Korea (1954–2025)
## 1. Study Area and Geographic Context
This analysis examines long-term surface air temperature changes in Seoul, South Korea (Station ID: 108, Songwol-dong station). Located in East Asia, Seoul has undergone rapid industrialization and urban expansion over the past several decades. Investigating Seoul's temperature trajectory allows us to observe both global climate change forcing and the local Urban Heat Island (UHI) effect.

### Data Source and Preprocessing Justification
The dataset was obtained from the [Korea Meteorological Administration (KMA)](https://www.kma.go.kr/eng/)
Automated Synoptic Observing System (ASOS), downloaded via the KMA Open MET Data Portal
([Temperature Analysis page](https://data.kma.go.kr/stcs/grnd/grndTaList.do), in Korean; accessed October 2026).

While observations began in late 1907, the historical time series contains critical observational gaps:
- **1907 & 2026:** Incomplete calendar years (1907 records began in October; 2026 is currently ongoing).
- **1950–1953 (Korean War Era):** Severe observational disruption resulted in extensive missing data (e.g., zero valid observations across 1951–1952).

To prevent artificial skewness in annual means, the analytical period was refined to **1954–2025**, providing a completely continuous 72-year record with 100% data completeness.

---

## 2. Plots: Data Cleaning & Trend Analysis

### Initial Exploration and Missing Data Anomalies
As illustrated below, raw aggregation without accounting for missing records during wartime creates extreme artificial troughs in annual temperature computations (notably the 1953 anomaly).

![Daily Temperature](img/01_daily_climate_missing.jpeg)

*Figure 1. Daily temperature series for Seoul showing observational disruptions during the early 1950s.*


<iframe src="img/03_hvplot_ann_missing_climate.html" width="100%" height="380px" frameborder="0"></iframe>

*Figure 2. Interactive unfiltered annual mean temperature showing extreme distortion caused by missing data during the Korean War.*

---

### Cleaned Annual Series (1954–2025)
Filtering for complete annual cycles yields a robust and continuous representation of interannual temperature variability in post-war Seoul.

![Clean Annual Series](img/04_ann_climate.jpeg)

*Figure 3. Cleaned annual average temperature series for Seoul (1954–2025).*

---

### Linear Regression Analysis (OLS Trend)
An ordinary least squares (OLS) linear regression was performed to quantify the rate of warming over the 72-year continuous period.

![Seoul Temperature Trend](img/06_seoul_temperature_trend.jpeg)

*Figure 4. Linear trend of annual average temperature in Seoul, South Korea (1954–2025).*

---

## 3. Findings and Interpretation

### Quantitative Evidence
- **Warming Rate (Slope):** +0.0343 °C/year (+0.343 °C/decade)
- **Statistical Significance:** R² = 0.614, p = 3.94 × 10⁻¹⁶ (p < 0.001)
- **Total Temperature Rise:** Over the 72-year study period, Seoul's mean annual temperature rose by approximately **2.47 °C**.

### Discussion: Regional vs. Global Warming Comparison

![Boulder Temperature Trend](img/boulder_temperature_trend.png)

*Figure 5. Linear trend of annual average temperature in Boulder, Colorado (Baseline).*

Comparing Seoul's warming rate to regional baselines such as Boulder, Colorado (which exhibited an increase of approximately 0.15 °C/decade as shown in Figure 5), Seoul has warmed at **more than twice the rate**. 

This accelerated warming is primarily attributed to two primary drivers:
1. **Macro-scale Climate Warming:** The Korean Peninsula has warmed faster than the global land average over the past century (Park et al., 2017), and long-term increases in temperature extremes across Korea and East Asia have been linked to greenhouse gas forcing (Min et al., 2015).
2. **Intense Urban Heat Island (UHI) Effect:** Post-war reconstruction and rapid economic growth intensified the UHI in the Seoul Metropolitan Area over 1962–2017 (Hong et al., 2019). High-density redevelopment has been shown to raise local minimum temperatures and anthropogenic heat emissions (Hong & Hong, 2016), while the expansion of impervious surfaces and loss of vegetation are associated with higher surface temperatures (Priyankara et al., 2019).

This statistical evidence confirms that high-density metropolitan areas experience compounded climate exposure due to local land surface transformations.

## References

- Hong, J.-W., & Hong, J. (2016). Changes in the Seoul Metropolitan Area urban heat environment with residential redevelopment. *Journal of Applied Meteorology and Climatology*, 55(5), 1091–1106. [https://doi.org/10.1175/JAMC-D-15-0321.1](https://doi.org/10.1175/JAMC-D-15-0321.1)
- Hong, J.-W., Hong, J., Kwon, E. E., & Yoon, D. K. (2019). Temporal dynamics of urban heat island correlated with the socio-economic development over the past half-century in Seoul, Korea. *Environmental Pollution*, 254, 112934. [https://doi.org/10.1016/j.envpol.2019.112934](https://doi.org/10.1016/j.envpol.2019.07.102)
- Min, S.-K., Son, S.-W., Seo, K.-H., Kug, J.-S., & An, S.-I. (2015). Changes in weather and climate extremes over Korea and possible causes: A review. *Asia-Pacific Journal of Atmospheric Sciences*, 51(2), 103–121. [https://doi.org/10.1007/s13143-015-0066-5](https://doi.org/10.1007/s13143-015-0066-5)
- Park, B.-J., Kim, Y.-H., Min, S.-K., Kim, M.-K., & Choi, Y. (2017). Long-term warming trends in Korea and contribution of urbanization: An updated assessment. *Journal of Geophysical Research: Atmospheres*, 122(20), 10637–10654. [https://doi.org/10.1002/2017JD027167](https://doi.org/10.1002/2017JD027167)
- Priyankara, P., Ranagalage, M., Dissanayake, D. M. S. L. B., Morimoto, T., & Murayama, Y. (2019). Spatial process of surface urban heat island in rapidly growing Seoul metropolitan area for sustainable urban planning using Landsat data (1996–2017). *Climate*, 7(9), 110. [https://doi.org/10.3390/cli7090110](https://doi.org/10.3390/cli7090110)
