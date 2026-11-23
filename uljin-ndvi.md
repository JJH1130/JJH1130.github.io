# How Did Vegetation Change After the 2022 Uljin Wildfire?

## 1. Background and Study Area
Uljin is a county on the east coast of South Korea, facing the East Sea. On March 4, 2022, a wildfire started in Uljin. It spread north to Samcheok and burned for about 213 hours, which made it the longest wildfire on record in Korea. The Korea Forest Service reported that 20,923 ha of forest burned (Asia Business Daily, 2022). A study using satellite images found a smaller burned area of 11,457 ha, because it used a different definition of burned area (Baek et al., 2022).

Most of the forest in this area was Korean red pine (Shin et al., 2024). Coniferous forests, such as pine, burned more severely than deciduous forests (Baek et al., 2022). To see how plants change after a fire, scientists often use the Normalized Difference Vegetation Index (NDVI). NDVI is calculated from satellite images and goes from -1 to 1. Higher values mean more green and healthy plants. Before the fire, NDVI in most mountain areas was above 0.6, but in areas that burned badly, it dropped below 0.2 (Shin et al., 2024).

Forests can take a long time to recover after a fire. After the 2000 East Coast wildfire in Korea, NDVI took about 9 years to return to normal in areas with low or moderate damage, and about 17 years in areas with high damage (Ryu et al., 2018).

In the Gila River assignment, NDVI increased after water came back. In Uljin, I expect NDVI to drop after the fire and then slowly increase again.

**Research question:** How much did vegetation (NDVI) drop after the 2022 Uljin wildfire, and how much has it recovered by 2025?

## 2. Data and Methods
- **Study area:** I drew a rectangle around the fire area on [geojson.io](https://geojson.io) using satellite images (Figure 1).
- **NDVI data:** I used NDVI from the Moderate Resolution Imaging Spectroradiometer (MODIS), a sensor on NASA's Terra satellite. The product is MOD13Q1 (version 061), which has 250m pixels and combines 16 days of images into one. I downloaded the data for July from 2019 to 2025 with NASA's Application for Extracting and Exploring Analysis Ready Samples (AppEEARS), using its API, a tool to request data with code. Each year has three 16-day images that cover July. I used the same month, July, every year so that the years can be compared fairly.
- **Burned area:** For each pixel, I averaged the nine July images from 2019–2021 (before the fire) and the nine July images from 2022–2024 (after the fire). Then I subtracted the before map from the after map to get the change in NDVI, and drew a boundary around the area where NDVI dropped the most. Because I chose this boundary from the NDVI drop, the drop itself is expected. So in the results, I focus on when the drop happened and how NDVI changed after it.
- **Comparison:** For each year, I averaged the three July images and all the pixels inside the burned area to get one mean NDVI value. I did the same for the rest of the rectangle (the unburned area), and then calculated the difference between the two.

The full code is available in [this notebook](https://github.com/JJH1130/jjh1130.github.io/blob/main/notebooks/uljin-ndvi.ipynb).

<iframe src="img/uljin-site-map.html" width="100%" height="450px" frameborder="0" scrolling="no"></iframe>

*Figure 1. The study area (white rectangle) around the 2022 Uljin wildfire. Basemap: Esri World Imagery.*

## 3. Results

### NDVI dropped sharply in the center of the study area

<iframe src="img/uljin-ndvi-change-map.html" width="100%" height="400px" frameborder="0" scrolling="no"></iframe>

*Figure 2. Change in mean July NDVI (2022–2024 minus 2019–2021). Pink means NDVI went down, and green means NDVI went up. The black line shows the burned area, which I drew based on the NDVI drop.*

NDVI dropped by more than 0.2 in the center of the study area, inside the black line. This is the area that burned in the fire. In the western part of the study area, NDVI went up a little, by about 0.1. This forest did not burn. The dark green and pink dots along the coast are pixels that mix land and sea, so they are not reliable.

### The burned forest is recovering, but slowly

<iframe src="img/uljin-ndvi-burned-unburned.html" width="100%" height="320px" frameborder="0" scrolling="no"></iframe>

*Figure 3. Mean July NDVI in the burned area and the unburned area, 2019–2025.*

Before the fire, the burned area had slightly higher NDVI than the unburned area. Since I chose the burned area from the NDVI drop, it is expected that NDVI there is lower after the fire. The more important points are the timing and the recovery. NDVI in the burned area stayed high until 2021 and then fell sharply in 2022, from about 0.83 to 0.64, the year of the fire. NDVI in the unburned area stayed almost the same (about 0.80 to 0.79). After that, NDVI in the burned area went up to about 0.71 in 2023 and 0.75 in 2025. In 2020, NDVI went down in both areas, so that drop was not caused by the fire.

<iframe src="img/uljin-ndvi-difference.html" width="100%" height="320px" frameborder="0" scrolling="no"></iframe>

*Figure 4. Difference in mean July NDVI between the burned and unburned areas (burned minus unburned).*

The difference was about +0.03 in 2021, but it fell to −0.144 in 2022. By 2025, it was about −0.10. A positive value means the burned area was greener than the unburned area, and a negative value means it was less green. So before the fire, the burned forest was a little greener than the forest around it, but after the fire, its NDVI was about 0.14 lower. This means the gap dropped by about 0.17 after the fire, and only about a quarter of it has come back in three years.

## 4. Interpretation
The NDVI drop in 2022 shows the clear effect of the wildfire. Since NDVI in the unburned area did not drop in 2022, the change was mainly caused by the fire. NDVI in the burned area started to go up only one year after the fire, which matches Shin et al. (2024).

However, the recovery is slow. After three years, only about a quarter of the gap has closed. The recovery was fastest in 2023 and then slowed down. This matches the study of the 2000 East Coast wildfire, where NDVI took 9 to 17 years to fully recover (Ryu et al., 2018). If the Uljin forest recovers at a similar speed, it may take about ten more years.

This result is the opposite of the Gila River case. In the Gila River Indian Community, NDVI went up because water came back to the farms. In Uljin, NDVI went down because the forest burned, and it is coming back slowly.

## 5. Limitations
- **Pixel size:** MODIS pixels are 250m, so one pixel can include both burned and unburned land.
- **Choosing the burned area from NDVI:** I drew the burned area where NDVI dropped the most, so the size of the drop may look larger than it really is. The boundary is in the right place, because it includes Buk-myeon, where the fire started (Baek et al., 2022). However, it is still a hand-drawn boundary. An official burned area map would be more accurate, but I could not find one from the Korean government that I could download, so I drew the boundary myself.
- **NDVI is not the whole forest:** NDVI shows how green the land is, not how big the trees are. Grasses and shrubs can make NDVI go up before trees grow back. Different parts of a forest recover at different speeds, so it is better to use more than one index (Ryu et al., 2018).

## References
- Asia Business Daily. (2022, March 13). *Longest-ever Uljin-Samcheok wildfire containment... "20,923 ha reduced to ashes"*. https://www.asiae.co.kr/en/article/2022031309334473240
- Baek, S., Lim, J., & Kim, W. (2022). Analysis on the fire progression and severity variation of the massive forest fire occurred in Uljin, Korea, 2022. *Forests*, 13(12), 2185. https://doi.org/10.3390/f13122185
- Ryu, J.-H., Han, K.-S., Hong, S., Park, N.-W., Lee, Y.-W., & Cho, J. (2018). Satellite-based evaluation of the post-fire recovery process from the worst forest fire case in South Korea. *Remote Sensing*, 10(6), 918. https://doi.org/10.3390/rs10060918
- Shin, S. S., Park, S. D., & Kim, G. (2024). Applicability comparison of GIS-based RUSLE and SEMMA for risk assessment of soil erosion in wildfire watersheds. *Remote Sensing*, 16(5), 932. https://doi.org/10.3390/rs16050932
