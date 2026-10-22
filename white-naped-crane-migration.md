# Seasonal Migration of the White-naped Crane in East Asia (2024)

## 1. Species and Study Area
The White-naped Crane (*Antigone vipio*) is a large crane that breeds in northeastern Mongolia, northeastern China, and southeastern Russia, and spends the winter in China, Korea, and Japan. It is listed as **Vulnerable** by the International Union for Conservation of Nature (IUCN), and its total population is more than 11,000 birds (International Crane Foundation, n.d.).

The species is divided into two groups. The western population migrates through China and winters in the middle Yangtze River valley. The eastern population, about 2,000 birds, migrates through the Korean Peninsula. Several hundred of them winter in the Demilitarized Zone (DMZ), and the rest continue to Kyushu, Japan (International Crane Foundation, n.d.). I saw White-naped Cranes wintering in the DMZ area in Korea in 2024, so I wanted to see whether this migration can be found in public observation data.

<video src="img/crane-dmz-2024.mp4" width="100%" autoplay loop muted playsinline></video>

*Figure 1. White-naped Cranes feeding near the DMZ, South Korea (winter 2024). Video taken by the author.*

**Research question:** When and where do White-naped Cranes move during the year, based on 2024 GBIF observations?

### Data and Preprocessing
- **Species observations:** I downloaded all 2024 White-naped Crane records with coordinates from the [Global Biodiversity Information Facility (GBIF)](https://www.gbif.org/) using the **pygbif** package (GBIF.org, 2026). GBIF lists *Antigone vipio* as a synonym of *Grus vipio*, so I used the accepted taxon key to include records under both names. The download includes **2,175 records**.
- **Ecoregions:** I grouped the observations by [RESOLVE Ecoregions 2017](https://storage.googleapis.com/teow2016/Ecoregions2017.zip), a global ecoregion map that has been widely used to depict species distributions (Dinerstein et al., 2017). Within one ecoregion, habitat conditions for a species should be fairly similar in the same season.

To prepare the data, I made three choices:
1. **Spatial join:** Each observation was assigned to the ecoregion that contains it.
2. **Removing rare records:** Ecoregion-month combinations with only one observation were removed, since a single record may be an outlier or error.
3. **Normalization:** GBIF records are spatially biased because of uneven sampling effort (Beck et al., 2014). To reduce this bias, I divided the number of observations by the mean for each ecoregion and the mean for each month.

After these steps, 58 combinations of ecoregion and month remained, and every month had data.

---

## 2. Interactive Migration Map

<iframe src="img/white-naped-crane-migration.html" width="100%" height="560px" frameborder="0"></iframe>

*Figure 2. Normalized White-naped Crane observations by ecoregion and month (2024). Use the slider to change the month. The color scale changes each month.*

---

## 3. Findings and Interpretation

### Seasonal Pattern
The map shows a clear seasonal movement between breeding grounds in the north and wintering grounds in the south.
- **Winter (December–February):** Observations are concentrated in the Korean Peninsula, southern Japan, and the middle and lower Yangtze River. In January, Japan had the most records (320 of 536), but the Korean Peninsula had the highest normalized value. This may be because the normalization reduces the effect of places that are always heavily observed, such as the feeding station near Izumi, Japan (International Crane Foundation, n.d.).
- **Spring migration (March–April):** In March, the highest values move to the North China Plain and the lower Yellow River. In April, the highest values appear in the Amur River basin in Russia, and the Korean Peninsula almost disappears from the map.
- **Breeding season (May–September):** Observations are concentrated in the steppes of eastern Mongolia, Inner Mongolia, and the Amur region. In June, 226 of 246 records were made in Mongolia.
- **Fall migration (October–November):** In October, the Korean Peninsula becomes the brightest area again. By November and December, the cranes have returned to Korea, Japan, and the Yangtze River.

### Comparison with Previous Research
The map shows two separate routes, which aligns with the two populations described in the previous research.

1. **Eastern route through Korea:** The Korean Peninsula still has observations in March and becomes bright again in October and November, while the Amur basin is bright in April. This matches satellite tracking of 15 cranes from Japanese wintering grounds, which showed that the DMZ, especially Panmunjom and Cheorwon, is the most important place for the cranes to rest during migration. The cranes spent up to 87.1% of their total migration time at these resting sites (Higuchi et al., 1996).
2. **Western route through China:** The North China Plain and the lower Yellow River are bright in March and November, and the Yangtze River is the brightest area in December. Jia et al. (2021) reported that the western population winters in the Yangtze River basin, mainly at Poyang Lake. Using satellite tracking, they found that this population changed its migration route, and they suggested that this was likely caused by wetland loss. For example, wetlands in the places where the cranes rest in Bohai Bay decreased by 42% between 1990 and 2010.
3. **Breeding grounds in Mongolia:** The bright areas in eastern Mongolia from May to September match the breeding area studied by Gilbert et al. (2016). They reported that the number of crane pairs along the Ulz River dropped from 42 in 2001 to 17 in 2011, during a drought that lasted at least ten years.

These results show that both the wintering sites (such as the DMZ) and the stopover and breeding wetlands are important for this species. Wetland loss in China and drought in Mongolia are threats along the migration route (Gilbert et al., 2016; Jia et al., 2021).

### Limitations
- **One year of data:** This analysis uses only 2024 records, so the pattern may differ in other years.
- **Sampling bias:** Even after normalization, GBIF records depend on where people observe and share data (Beck et al., 2014). For example, many cranes gather at a feeding station near Izumi, Japan, which may attract more observers (International Crane Foundation, n.d.).
- **Unusual records:** In February, Hokkaido has the highest value, even though it is not a major wintering site. This may come from a small number of records that became large after normalization, or from errors.
- **Color scale:** The color scale changes each month, and in August only one ecoregion has data. So the map is better for comparing places within a month than for comparing months.

---

## References

- Beck, J., Böller, M., Erhardt, A., & Schwanghart, W. (2014). Spatial bias in the GBIF database and its effect on modelling species' geographical distributions. *Ecological Informatics*, 19, 10–15. [https://doi.org/10.1016/j.ecoinf.2013.11.002](https://doi.org/10.1016/j.ecoinf.2013.11.002)
- Dinerstein, E., Olson, D., Joshi, A., Vynne, C., Burgess, N. D., Wikramanayake, E., Hahn, N., et al. (2017). An ecoregion-based approach to protecting half the terrestrial realm. *BioScience*, 67(6), 534–545. [https://doi.org/10.1093/biosci/bix014](https://doi.org/10.1093/biosci/bix014)
- GBIF.org. (2026). *GBIF occurrence download* [Data set]. https://doi.org/10.15468/dl.kp4bhp
- Gilbert, M., Buuveibaatar, B., Fine, A. E., Jambal, L., & Strindberg, S. (2016). Declining breeding populations of White-naped Cranes in Eastern Mongolia, a ten-year update. *Bird Conservation International*, 26(4), 490–504. [https://doi.org/10.1017/S0959270915000301](https://doi.org/10.1017/S0959270915000301)
- Higuchi, H., Ozaki, K., Fujita, G., Minton, J., Ueta, M., Soma, M., & Mita, N. (1996). Satellite tracking of White-naped Crane migration and the importance of the Korean Demilitarized Zone. *Conservation Biology*, 10(3), 806–812.
- International Crane Foundation. (n.d.). *White-naped crane*. Retrieved October 23, 2026, from [https://savingcranes.org/species/white-naped-crane/](https://savingcranes.org/species/white-naped-crane/)
- Jia, Y., Liu, Y., Jiao, S., Guo, J., Lu, C., Zhou, Y., Wang, Y., Lei, G., Wen, L., & Mo, X. (2021). Shifting of the migration route of White-naped Crane (*Antigone vipio*) due to wetland loss in China. *Remote Sensing*, 13(15), 2984. [https://doi.org/10.3390/rs13152984](https://doi.org/10.3390/rs13152984)
