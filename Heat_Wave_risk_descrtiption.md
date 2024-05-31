Risk Assessment for Heat-Wave 
=======================
**Heat-wave definition**

Multiple methodologies can define the heat wave. But in general, the heat-wave is determined by the air temperature and the duration (days) thresholds. 

**Risk Assessment methodology**

This workflow consists of two parts: 1. Hazard and 2.Risk Assessment:

**1. Hazard assessment**
=======================
In Hazard assessment, we use 3 different methodologies ([Euroheat](https://climate-adapt.eea.europa.eu/en/metadata/tools/euroheat-online-heatwave-forecast), [Peseta IV](https://de.wikipedia.org/wiki/Peseta_IV), [Xclim](https://xclim.readthedocs.io/en/stable/indicators.html) ) for the heat-wave estimation. The user can choose from the most suitable methods for his needs. These methodologies differ in the input data, temperature treshold, duration thresholds, computing algorithm, and results. So in the first step, the user will choose the methodology based on the pros and cons of each methodology. Each methodology works with the air temperature data for the Representative Concentration Pathways (RCPs) climate scenarios 4.5 (medium) and 8.5 (extreme) [[more about RCPs](https://en.wikipedia.org/wiki/Representative_Concentration_Pathway)]. 

Results from hazard assessment give you information about the heat-wave occurrence in the reference period 1971-2000 and three projection periods 2011-2040, 2041-2070, and 2071-2100 represented in yearly and monthly (only Peseta IV) values. 

**Data for Hazard assessment**

You can find more information about the data in the following links.

- **EUROheat [[source](https://cds.climate.copernicus.eu/cdsapp#!/dataset/sis-heat-and-cold-spells?tab=form)]**
- **PESETA IV [[source](https://cds.climate.copernicus.eu/cdsapp#!/dataset/projections-cordex-domains-single-levels?tab=form)]**
- **XCLIM [[source](https://cds.climate.copernicus.eu/cdsapp#!/dataset/projections-cordex-domains-single-levels?tab=form)]**

**2. Risk assessment** 
=======================
Based on the current climate scenario the occurrence of the heat-wave phenomenon should be more frequent in the future in Europe. The main problems connected with Heat-wave events are the overheating of the urban areas, which lowers the comfort of living or causes health issues [[Integrated Assessment of Urban Overheating Impacts on Human Life](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2022EF002682)], drought, and water scarcity. Nowadays, there are a lot of studies and methodologies on how we can mitigate the influence of these events. 

In the risk assessment, we focus on the estimation of the:

- **Exposure** = Heat islands (identification of the overheated places)
- **Vulnerability** = Vulnerable population (people over 65 and under 5 years old)
- **Risk** = Exposure x Vulnerability map for human health (You need to consider the **Probability** from the results of the Hazard workflow. However, due to the coarse resolution of Hazard data, you will not see any differences in the different parts of the cities. But you can see the differences in the regional scale.)

**(Bonus)** Vegetation characteristics = NDVI vegetation characteristics (Current health condition of the vegetation)

**Data for Risk assessment**

- **Exposure data** = Heat islands estimation from the Landsat8 satellite imagery [[source]()]
  - Estimation of the Land surface temperature
  - Resolution 30x30m
  - Period: 2013-2021 (till now from Landsat9, need another processing)
  - **Data limitations**: Problems with clouds, 16-day time step (not daily data), The resolution of 30x30 meters does not catch all    the details   

- **Vulnerability** = Vulnerable population groups (elderly people over 65 years and under 5 years) [[source]()]
  - Data from the WorldPop website
  - Resolution 100x100m
  - **Data limitations**: Resolution of 100x100m, data for the year 2020 (might have changed)

- **(Bonus)** Vegetation characteristics data from Sentinel2 satellite imagery [[source]()]
  - Estimation of the Normalize Difference Vegetation Index (NDVI) for the estimation of vegetation health
  - Resolution 10x10m 
  - **Data limitations**: Problems with clouds, 8-day time step (not daily data), The resolution of 10x10 meters does not catch all     details
