# Dengue forecasting tutorial — dataset descriptors and inventory

This folder contains the **epidemiological training data** for the tutorial ([`BRA_epi_training.csv`](BRA_epi_training.csv)) and the following **descriptors** for all covariate datasets (climate, socioeconomic, demographic) used in the practical. The **covariate NetCDF files** are not all stored in this repository: one dataset is too large to host here, and for the tutorial students obtain the data (including that file) from the **Global.health data portal**: [https://sim-dev-data.covid-19.global.health/data-downloads](https://sim-dev-data.covid-19.global.health/data-downloads). Sign in with a Google account; access may need to be granted by an admin. Brazil files use the prefix `BRA`.

---

Covariate data are in **NetCDF** format (`.nc`); the epidemiological data are **CSV**. Each dataset has its own license and citation (given below). For the tutorial you use Brazil files only; on the Global.health portal they have the prefix `BRA` (e.g. `BRA-reanalysis_monthly.zs.nc`).

NetCDF files contain variables indexed by *time* (usually monthly) and *region* (administrative unit ID). Static datasets have only *region*. The sections below describe each dataset: what it contains, units, and how to cite it.

## Inventory (Brazil tutorial)

Non-epidemiological datasets you may use for the Brazil tutorial (download from Global.health; filename pattern `BRA-*.zs.nc` or `BRA_*.zs.nc`):

- ccvi, gdp_pc, population, reanalysis_monthly, seasonal_forecast_monthly  
- spa01, spa03, spa06, spa12 (Standardized Precipitation Index)  
- spe01, spe03, spe06, spe12 (Standardized Precipitation-Evapotranspiration Index)  
- surv_wmean, swvl1, urban, w_piped  


## Datasets

### reanalysis_monthly

- *Dataset*: Monthly averages of ERA5 reanalysis
- *Temporal resolution*: monthly
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variables:
- t2m: 2 meters air temperature (K)
- rh: Relative humidity, expressed as a fraction between 0 and 1 (unitless)
- tp: Total precipitation (m), using `remapdis` for resampling and `area_weighted_sum` for zonal statistics

*Dataset notes*: Relative humidity was calculated using
`metpy.calc.relative_humidity_from_dewpoint()`

If using this dataset, please cite:

> Hersbach, H., Bell, B., Berrisford, P., Biavati, G., Horányi, A., Muñoz
> Sabater, J., Nicolas, J., Peubey, C., Radu, R., Rozum, I., Schepers, D.,
> Simmons, A., Soci, C., Dee, D., Thépaut, J-N. (2023): ERA5 monthly averaged
> data on single levels from 1940 to present. Copernicus Climate Change Service
> (C3S) Climate Data Store (CDS), DOI: 10.24381/cds.f17050d7 (Accessed on
> 2025-11-18)

### seasonal_forecast_monthly

- *Dataset*: Seasonal monthly forecasts (Copernicus)
- *Temporal resolution*: monthly
- *Temporal extent*: 2015-2025
- *Coordinates*: (time, month, region)
- *License*: CC-BY-4.0

Variables:
- t2m: 2 meters air temperature (K)
- mn2t24: Minimum air temperature in a 24h period (K)
- mx2t24: Maximum air temperature in a 24h period (K)
- rh: Relative humidity, expressed as a fraction between 0 and 1 (unitless)
- tp: Total precipitation (m), using `remapdis` for resampling and `area_weighted_sum` for zonal statistics

*Dataset notes*: The additional coordinate `month` in this dataset represents
the forecast lead time and ranges from 1..6 for one to six months ahead forecast
starting at a particular `time` coordinate. Relative humidity was calculated
using `metpy.calc.relative_humidity_from_dewpoint()`. Total precipitation was
calculated from the source precipitation rate variable (`tprate`) by multiplying
the number of seconds for each forecast duration.

If using this dataset, please cite:

> Copernicus Climate Change Service, Climate Data Store, (2018): Seasonal
> forecast monthly statistics on single levels. Copernicus Climate Change
> Service (C3S) Climate Data Store (CDS). DOI: 10.24381/cds.68dd14c3 (Accessed
> on 2025-11-25)

### spa01

- *Dataset*: 10-day Standardized Precipitation Index, 1-month accumulation
  period (SPI-1), ERA5
- *Temporal resolution*: ~every 10 days, 01, 11, 21 of a month
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variable: spa01 (unitless)

*Dataset notes*: Interpolation for NA values was performed with manual checks to ensure interpolation only covered a small region.

If using this dataset, please cite:

> European Drought Observatory, https://drought.emergency.copernicus.eu (C)
> European Commission - JRC, 2012 - 202x.

The following reference must be mentioned as well:

> C. Cammalleri, P. Barbosa, J. V. Vogt. (2020) Evaluating simulated daily
> discharge for operational hydrological drought monitoring in the Global
> Drought Observatory (GDO). Hydrological Sciences Journal 65:8, pages
> 1316-1325.

### spa03

- *Dataset*: 10-day Standardized Precipitation Index, 3-months accumulation period (SPI-3), ERA5
- *Temporal resolution*: ~every 10 days, 01, 11, 21 of a month
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variable: spa03 (unitless)

*Dataset notes*: Interpolation for NA values was performed with manual checks to ensure interpolation only covered a small region.

If using this dataset, please cite:

> European Drought Observatory, https://drought.emergency.copernicus.eu (C)
> European Commission - JRC, 2012 - 202x.

The following reference must be mentioned as well:

> C. Cammalleri, P. Barbosa, J. V. Vogt. (2020) Evaluating simulated daily
> discharge for operational hydrological drought monitoring in the Global
> Drought Observatory (GDO). Hydrological Sciences Journal 65:8, pages
> 1316-1325.

### spa06

- *Dataset*: Standardized Precipitation Index, 6-months accumulation period (SPI-6), ERA5
- *Temporal resolution*: monthly
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variable: spa06 (unitless)

*Dataset notes*: Interpolation for NA values was performed with manual checks to ensure interpolation only covered a small region.

If using this dataset, please cite:

> European Drought Observatory, https://drought.emergency.copernicus.eu (C)
> European Commission - JRC, 2012 - 202x.

The following reference must be mentioned as well:

> C. Cammalleri, P. Barbosa, J. V. Vogt. (2020) Evaluating simulated daily
> discharge for operational hydrological drought monitoring in the Global
> Drought Observatory (GDO). Hydrological Sciences Journal 65:8, pages
> 1316-1325.

### spa12

- *Dataset*: Standardized Precipitation Index, 12-months accumulation period (SPI-12), ERA5
- *Temporal resolution*: monthly
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variable: spa12 (unitless)

*Dataset notes*: Interpolation for NA values was performed with manual checks to ensure interpolation only covered a small region.

If using this dataset, please cite:

> European Drought Observatory, https://drought.emergency.copernicus.eu (C)
> European Commission - JRC, 2012 - 202x.

The following reference must be mentioned as well:

> C. Cammalleri, P. Barbosa, J. V. Vogt. (2020) Evaluating simulated daily
> discharge for operational hydrological drought monitoring in the Global
> Drought Observatory (GDO). Hydrological Sciences Journal 65:8, pages
> 1316-1325.

### spe01

- *Dataset*: 10-day Standardized Precipitation-Evapotranspiration Index,
  1-month accumulation period (SPEI-1), ERA5
- *Temporal resolution*: ~every 10 days, 01, 11, 21 of a month
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variable: spe01 (unitless)

*Dataset notes*: Interpolation for NA values was performed with manual checks to ensure interpolation only covered a small region. Data was [clipped to -3.09 to 3.09](https://github.com/monocongo/climate_indices/blob/master/src/climate_indices/indices.py), where 90% of SPEI values lie, to avoid `inf` propagation.

If using this dataset, please cite:

> European Drought Observatory, https://drought.emergency.copernicus.eu (C)
> European Commission - JRC, 2012 - 202x.

The following references must be mentioned as well:

> C. Cammalleri, P. Barbosa, J. V. Vogt. (2020) Evaluating simulated daily
> discharge for operational hydrological drought monitoring in the Global
> Drought Observatory (GDO). Hydrological Sciences Journal 65:8, pages
> 1316-1325.

> Vicente-Serrano S.M., Santiago Beguería, Juan I. López-Moreno, (2010) A
> Multi-scalar drought index sensitive to global warming: The Standardized
> Precipitation Evapotranspiration Index - SPEI. Journal of Climate 23:
> 1696-1718.

### spe03

- *Dataset*: 10-day Standardized Precipitation-Evapotranspiration Index,
  3-month accumulation period (SPEI-3), ERA5
- *Temporal resolution*: ~every 10 days, 01, 11, 21 of a month
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variable: spe03 (unitless)

*Dataset notes*: Interpolation for NA values was performed with manual checks to ensure interpolation only covered a small region. Data was [clipped to -3.09 to 3.09](https://github.com/monocongo/climate_indices/blob/master/src/climate_indices/indices.py), where 90% of SPEI values lie, to avoid `inf` propagation.

If using this dataset, please cite:

> European Drought Observatory, https://drought.emergency.copernicus.eu (C)
> European Commission - JRC, 2012 - 202x.

The following references must be mentioned as well:

> C. Cammalleri, P. Barbosa, J. V. Vogt. (2020) Evaluating simulated daily
> discharge for operational hydrological drought monitoring in the Global
> Drought Observatory (GDO). Hydrological Sciences Journal 65:8, pages
> 1316-1325.

> Vicente-Serrano S.M., Santiago Beguería, Juan I. López-Moreno, (2010) A
> Multi-scalar drought index sensitive to global warming: The Standardized
> Precipitation Evapotranspiration Index - SPEI. Journal of Climate 23:
> 1696-1718.

### spe06

- *Dataset*: Standardized Precipitation-Evapotranspiration Index, 6-months
  accumulation period (SPEI-6), ERA5
- *Temporal resolution*: monthly
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variable: spe06 (unitless)

*Dataset notes*: Interpolation for NA values was performed with manual checks to ensure interpolation only covered a small region. Data was [clipped to -3.09 to 3.09](https://github.com/monocongo/climate_indices/blob/master/src/climate_indices/indices.py), where 90% of SPEI values lie, to avoid `inf` propagation.

If using this dataset, please cite:

> European Drought Observatory, https://drought.emergency.copernicus.eu (C)
> European Commission - JRC, 2012 - 202x.

The following references must be mentioned as well:

> C. Cammalleri, P. Barbosa, J. V. Vogt. (2020) Evaluating simulated daily
> discharge for operational hydrological drought monitoring in the Global
> Drought Observatory (GDO). Hydrological Sciences Journal 65:8, pages
> 1316-1325.

> Vicente-Serrano S.M., Santiago Beguería, Juan I. López-Moreno, (2010) A
> Multi-scalar drought index sensitive to global warming: The Standardized
> Precipitation Evapotranspiration Index - SPEI. Journal of Climate 23:
> 1696-1718.

### spe12

- *Dataset*: Standardized Precipitation-Evapotranspiration Index, 12-months
  accumulation period (SPEI-12), ERA5
- *Temporal resolution*: monthly
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variable: spe12 (unitless)

*Dataset notes*: Interpolation for NA values was performed with manual checks to ensure interpolation only covered a small region. Data was [clipped to -3.09 to 3.09](https://github.com/monocongo/climate_indices/blob/master/src/climate_indices/indices.py), where 90% of SPEI values lie, to avoid `inf` propagation.

If using this dataset, please cite:

> European Drought Observatory, https://drought.emergency.copernicus.eu (C)
> European Commission - JRC, 2012 - 202x.

The following references must be mentioned as well:

> C. Cammalleri, P. Barbosa, J. V. Vogt. (2020) Evaluating simulated daily
> discharge for operational hydrological drought monitoring in the Global
> Drought Observatory (GDO). Hydrological Sciences Journal 65:8, pages
> 1316-1325.

> Vicente-Serrano S.M., Santiago Beguería, Juan I. López-Moreno, (2010) A
> Multi-scalar drought index sensitive to global warming: The Standardized
> Precipitation Evapotranspiration Index - SPEI. Journal of Climate 23:
> 1696-1718.

### swvl1

- *Dataset*: Volumetric soil water layer 1
- *Temporal resolution*: monthly
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0
- *No spatial extent*, this is global data

Variables: swvl1 (m**3 m**-3)

*Dataset notes*: Data was clipped to (0, 1) post-processing to remove spurious negative values.

If using this dataset, please cite:

> Hersbach, H., Bell, B., Berrisford, P., Biavati, G., Horányi, A., Muñoz
> Sabater, J., Nicolas, J., Peubey, C., Radu, R., Rozum, I., Schepers, D.,
> Simmons, A., Soci, C., Dee, D., Thépaut, J-N. (2023): ERA5 monthly averaged
> data on single levels from 1940 to present. Copernicus Climate Change Service
> (C3S) Climate Data Store (CDS), DOI: 10.24381/cds.f17050d7 (Accessed on
> 2025-11-18)


### population

- *Dataset*: Population count, density and shapefile area
- *Temporal resolution*: yearly
- *Temporal extent*: 2015-2025
- *License*: CC-BY-4.0

Variables:
- pop_count: Population count from constrained estimates (unitless)
- area: Area of administrative divisions in square kilometers in [EPSG:8857](https://epsg.io/8857) (km^2)
- pop_density: Population density, derived from pop_count divided by area (km^{-2})

*Dataset notes*: No resampling was performed for this dataset, and the `sum`
operation was used to aggregate population counts in an administrative level.

If using this dataset, please cite:

> Bondarenko M., Priyatikanto R., Tejedor-Garavito N., Zhang W., McKeen T.,
> Cunningham A., Woods T., Hilton J., Cihan D., Nosatiuk B., Brinkhoff T.,
> Tatem A., Sorichetta A.. Constrained estimates of 2015-2030 total number of
> people per grid square at a resolution of 30 arc (approximately 1km at the
> equator) R2025A version v1. Global Demographic Data Project - Funded by The
> Bill and Melinda Gates Foundation (INV-045237). WorldPop - School of
> Geography and Environmental Science, University of Southampton.
> DOI:10.5258/SOTON/WP00840

### urban

- *Dataset*: Fraction of urban areas
- *Temporal resolution*: static
- *Temporal extent*: static
- *License*: CC-BY-4.0

Variables: urban (unitless)

*Dataset notes*: The source GeoTIFF file in WGS84 was converted to NetCDF with
urban=1 and setting rural=0 (was 2 in the original data). Zonal statistics
(averaging) was performed without resampling to population density due to
dataset size, and also as urban/rural and population density would be
correlated. Grid cells without information (NaN) were considered non-urban (0).

If using this dataset, please cite:

> Liu, Z., Huang, S., Fang, C. et al. Global urban and rural settlement dataset
> from 2000 to 2020. Sci Data 11, 1359 (2024).
> https://doi.org/10.1038/s41597-024-04195-y

### ccvi

- *Dataset*: Climate Conflict Vulnerability Index
- *Temporal resolution*: quarterly
- *Temporal extent*: 2015-2023
- *License*: CC-BY-NC-4.0

Variables (units, description)
- VUL_socioeconomic_deprivation: Index of socioeconomic deprivation
- VUL_socioeconomic_inequality: Index of socioeconomic inequality

*Note*: One municipality for Brazil (Fernando de Noronha), which is an archipelago off the coast has no data from CCVI.

If using this dataset, please cite:

> Mittermaier, D; Merschroth, S; Šedová, B; Auer, C; Bohne, T; Ferri, S;
> Slouma, S; Michelini, S; Gottwick, V. (2025). The Climate Conflict
> Vulnerability Index (CCVI) - Technical Documentation v1.5. Available online
> at climate-conflict.org

### gdp_pc

- *Dataset*: Gross Domestic Product per capita, by purchasing power parity (PPP)
- *Temporal resolution*: yearly
- *Temporal extent*: 2015-2022
- *License*: CC-BY-4.0

Variable: gdp_pc (USD in 2017 international dollars)

If using this dataset, please cite:

> Kummu, M., Kosonen, M. & Masoumzadeh Sayyar, S. 2025.
> Downscaled gridded global dataset for gross domestic product (GDP)
> per capita PPP over 1990–2022. Scientific Data 12: 178.
> https://doi.org/10.1038/s41597-025-04487-x

### surv_wmean

- *Dataset*: Surveillance and reporting capacity
- *Temporal resolution*: static (2025)
- *Temporal extent*: static
- *License*: CC-BY-4.0

Variable: surv_mean (fraction between 0 and 1)

If using this dataset, please cite:

> Lim, A., Shearer, F.M., Sewalk, K. et al. The overlapping global distribution
> of dengue, chikungunya, Zika and yellow fever. Nat Commun 16, 3418 (2025).
> https://doi.org/10.1038/s41467-025-58609-5

### w_piped

- *Dataset*: Access to drinking water and sanitation facilities
- *Temporal resolution*: yearly, 2000-2017
- *Temporal extent*: static
- *License*: unknown

Variable: w_piped (access to piped water, percentage)

*Dataset notes*: We use a static snapshot by averaging data from 2015-2017 for
`w_piped` and using population data from 2016 as the weighting raster.

If using this dataset, please cite:

> Deshpande, A., Miller-Petrie, M. K., Lindstedt, P. A., Baumann, M. M.,
> Johnson, K. B., Blacker, B. F., ... & Darwish, A. H. (2020). Mapping
> geographical inequalities in access to drinking water and sanitation facilities
> in low-income and middle-income countries, 2000–17. The Lancet Global Health,
> 8(9), e1162-e1185.