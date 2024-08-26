# Heatwaves

## Methodology and data overview

This workflow is designed to help in exploring the local and regional risks presented by heatwaves, and assessing the impact of climate change on the heatwave hazard.

A heatwave is defined by the maximum and minimum daily temperature exceeding a certain threshold for a certain minimum amount of time. Various definitions are used in different methodologies for heatwave risk assessments, and in this workflow, we will explore the heatwave hazard based on several commonly used methodologies. The risk assessment focuses on the health risks presented to vulnerable populations.

### Heatwave hazard assessment under climate change

#### Heatwave hazard assessment open data products
There are several applications available online that allow the user to explore heatwave hazards for European regions without the need to perform their own calculations. Below is an overview of such resources. We recommend to explore these resources first, before using the more detailed CLIMAAX workflow.

The resources below provide information on heatwave indicators that are already aggregated to specific locations or regions using a specific methodology. This may not be sufficient for a more detailed assessment, which is why the CLIMAAX workflow is provided - it allows for more flexibility in analyzing the data with the possibility of selecting specific definitions of heatwave events (i.e. the thresholds for temperature and time duration) and defining your area of interest. 

**Resources available on the Copernicus Climate Data Store (C3S):**

 - [Heat wave days and heat related mortality for nine European cities](https://cds.climate.copernicus.eu/cdsapp#!/software/app-health-urban-heat-related-mortality-projections?tab=app).
 Data for Valencia, Barcelona, Roma, Milan, Munich, Paris, Athens, London and  Budapest derived from climate projections.  

 - [Heat wave days for Europe derived from ERA5 reanalysis - NUTS 3 level](https://cds.climate.copernicus.eu/cdsapp#!/software/app-health-heat-waves-current-climate?tab=app). 
 This application allows users to explore the past number of heat waves in European countries based on the historical reanalysis (ERA5), where the heatwaves are defined using two European-wide definitions: the Climatological EURO-CORDEX and EuroHEAT project definition, and one set of National definitions which are available for a limited number of European countries.

 - [Heat wave days for European countries derived from climate projections](https://cds.climate.copernicus.eu/cdsapp#!/software/app-health-heat-waves-projections?tab=app)
This application is an exploratory tool for future heat waves and cold spells derived from climate projections. This dataset provides 30-year rolling means of the number of heat wave days based on bias-adjusted output from the EURO-CORDEX ensemble of climate models.

**Resources available from ClimateAdapt:**

 - [Heat days occurrence in the past based on the Universal Thermal Comfort Index](https://climate-adapt.eea.europa.eu/en/metadata/indicators/high-utci-days).
 - [Heat days occurrence in the future climate scenarios based on the Apparent Temperature Heatwave Days Index](https://climate-adapt.eea.europa.eu/en/metadata/indicators/apparent-temperature-heatwave-days)
 - [Occurence of tropical nights under future climate scenarios](https://climate-adapt.eea.europa.eu/en/observatory/++aq++metadata/indicators/tropical-nights/)

#### CLIMAAX workflow: hazard assessment using EURO-CORDEX climate data
In the CLIMAAX workflow (in the following pages) we demonstrate how EURO-CORDEX data can be processed to assess heatwave hazard using two different methodologies: EuroHEAT and Xclim. The user can choose to apply one of these methodologies based on their preferred heatwave definition. The methodologies differ in terms of the required input data, temperature thresholds, duration thresholds, computing algorithm, and results.

[EuroHEAT](https://climate-adapt.eea.europa.eu/en/metadata/tools/euroheat-online-heatwave-forecast) defines the heatwave as a period where the maximum apparent and the minimum temperature is over the 90th percentile of the monthly distribution for at least two days. The monthly distribution is based on 30-year time series of daily temperatures in the recent historical climate (1971-2000). Using the EuroHEAT workflow is recommended because it utilizes data from multiple regional climate models to provide more reliable results, whereas the Xclim workflow relies on only one regional model. 

[Xclim](https://xclim.readthedocs.io/en/stable/indicators.html) project defines  a heatwave based on user-defined absolute temperature thresholds for the maximum and minimum daily temperatures (i.e. day and night temperatures), and a minimum time duration (e.g. 2 or 3 days). Using absolute thresholds for temperature requires input in terms of temperature thresholds, which are typically specific to a region and based on expected health impacts.

We use the climate scenarios RCP4.5 (medium) and RCP8.5 (extreme) to compare the effect of different climate scenarios ([more about RCPs](https://en.wikipedia.org/wiki/Representative_Concentration_Pathway)).

As a result of the hazard assessment, we can obtain information about the heatwave frequency of occurrence in the reference period of 1971-2000 and three future periods: 2011-2040, 2041-2070 and 2071-2100. This result is based on model data for climate projections.

##### Source datasets in this workflow
 Xclim methodology in this workflow uses the [EURO-CORDEX data](https://cds-beta.climate.copernicus.eu/datasets/projections-cordex-domains-single-levels?tab=overview).

Heatwave data prepared by the EuroHEAT project is directly available from the [dedicated dataset](https://cds-beta.climate.copernicus.eu/datasets/sis-heat-and-cold-spells?tab=overview) on the Copernicus Data Store. This data is also based on EURO-CORDEX data.

Both methodologies are thus based on the EURO-CORDEX climate projections data. Please note that the resolution of this data is 12x12km, and it is not suitable for accurately evaluating heat wave risks inside cities, because the dataset does not take into account the urban heat-island effect.

### Risk assessment methodology based on historical high-resolution data
One of the main negative impacts of heatwaves is the overheating of the urban areas, which lowers the comfort of living and can pose a threat to human health, especially in vulnerable populations, but also droughts and water scarcity (see also: [Integrated Assessment of Urban Overheating Impacts on Human Life](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2022EF002682)).

In the risk assessment example presented in this workflow, we focus on estimating risk based on population exposure and vulnerability, combined with high-resolution observation data for the temperature (hazard). By combining this assessment with the hazard assessment on changes in future heatwave frequency, it is possible to better estimate the future risks.

As output of the risk assessment, you obtain information about the overheated areas, overlapping with information on the vulnerable population groups. 

To assess risk, we use a 10+10 risk matrix, which consists of exposure (level of exposure to heat based on land surface temperature data) and vulnerability (vulnerable population groups based on world population data). The heat exposure data were divided into 10 groups based on the land surface temperature thresholds (1-2. Very low <20-25°C, 3-4. Low 25-35°C, 5-6. Medium 35-45°C, 7-8. High 45-55°C, 9-10. Very High 55-60<°C), these thresholds can be changed and values will depend on the selected area (more information in the risk assessment workflow). The vulnerability data were divided into 10 equally-spaced intervals based on the selected area.  

![heatwave ilustration](https://github.com/CLIMAAX/HEATWAVES/blob/main/Images/risk_matrix_10to10.png?raw=true "Risk matrix example")

#### Risk assessment datasets and limitations

In the risk assessment, we use the information on heat islands based on the [Landsat8 satellite imagery](https://rslab.gr/Landsat_LST.html) to represent **exposure**. This dataset estimates the land surface temperature with a spatial resolution of 30x30m for the period 2013-2021. This dataset is available with a 16-day time step. Please note that this is satellite-derived data and some inaccuracy can be caused by missing data on cloudy days.

**Vulnerability** is represented by the WorldPop dataset on vulnerable population groups (people older than 65 and people younger than 5 years old). The spatial resolution of this data is 100x100m. We use the data for the year 2020.

### Risk assessment methodology based on EuroHEAT climate projections at the regional level

The results of this workflow provide insights into the relative changes in heatwave occurrence based on the EuroHEAT climate projections data, the distribution of vulnerable population groups (Worldpop), and the projected heatwave risk for these vulnerable groups.

These findings help to better understand the projected magnitude of change in heatwave occurrence and highlight areas with a higher concentration of vulnerable population groups. Additionally, this workflow demonstrates the methodology for combining these two sets of information using a 10+10 risk matrix.

It is important to note that the level of risk is dependent on the area selected at the beginning of the analysis. This means that the risk level only reflects differences between the chosen regions.


## Structure of the workflow
This workflow consists of several parts, where the user is guided in performing a risk assessment for heat waves. Separate notebooks are available for the two methods of heat wave hazard estimation, followed by notebooks for estimating the level of risk to the population based on satellite data (local level), and the level of risk to the population based on the EuroHEAT data (regional level).

In the next pages you will find:
1. Heatwave hazard assessment using EuroHEAT methodology ([link to notebook on GitHub](https://github.com/CLIMAAX/HEATWAVES/blob/review_edits/heat_wave_hazard_assessment_euroheat.ipynb))
2. Heatwave hazard assessment using Xclim methodology ([link to notebook on GitHub](https://github.com/CLIMAAX/HEATWAVES/blob/review_edits/heat_wave_hazard_assessment_xclim.ipynb)
3. Risk assessment using satellite-derived data ([link to notebook on GitHub](https://github.com/CLIMAAX/HEATWAVES/blob/review_edits/heat_wave_risk_assessment.ipynb))

## Outputs of the workflow

The heatwave **hazard** workflow gives you the information about the heatwave occurrence at a yearly temporal resolution, with the reference period of 1971-2000 and future periods of 2011-2040, 2041-2070, and 2071-2100 under two climate scenarios: RCP4.5 and RCP8.5. This workflow allows you to modify the temperature and duration thresholds that specify the heatwave events according to your needs, you can define which thresholds are best suited for your region. The results provide you the information on how often you can expect heatwaves in the future. The duration of the heatwaves (in days) is also important to estimate possible heatwave events severity. 

The heatwave **risk** workflow provides you with information important to estimate which areas in your region are most exposed to the heat. By combining this with the distribution of vulnerable groups of the population, you can create a risk map for your selected area. Together with the results of the hazard workflow, you will get information both on the future heatwave hazard and the areas most exposed to this hazard under the current and future climate. The risk assessment at the regional level provides information about the projected heatwave occurrence changes for the near and further future with the combination of the distribution of the vulnerable groups at the regional level. 

## Authors of the workflow
This workflow was developed by [KAJO services](https://www.kajoservices.com/). The main contributors to the workflow are:

Martin Kuban, KAJO services.
Milan Kalas, KAJO services.
Natalia Aleksandrova, Deltares.

## References

Euroheat: 11.6.2024 [[source](https://confluence.ecmwf.int/display/CKB/Heat+waves+and+cold+spells+in+Europe+derived+from+climate+projections+documentation#heading-3References)]

XCLIM: 11.6.2024 [[source](https://cds-beta.climate.copernicus.eu/datasets/projections-cordex-domains-single-levels?tab=overview)]

RSLAB, Land surface Temperature, based on the Landsat8 imagery: 11.6.2024 [[source](https://rslab.gr/Landsat_LST.html)]

Humdata: world population data. Distribution of the critical groups of the population. 11.6.2024 [source](https://data.humdata.org/dataset/?dataseries_name=Data%20for%20Good%20at%20Meta%20-%20High%20Resolution%20Population%20Density%20Maps%20and%20Demographic%20Estimates&dataseries_name=WorldPop%20-%20Age%20and%20sex%20structures&dataseries_name=WorldPop%20-%20Population%20Density&groups=svk&res_format=GeoTIFF&q=&sort=last_modified%20desc&ext_page_size=25)

