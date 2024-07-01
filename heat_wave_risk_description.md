# Heatwaves

## Methodology and data overview

This workflow is designed to help in exploring the local and regional risks presented by heatwaves, and assessing the impact of climate change on the heatwave hazard.

A heatwave is defined by the maximum daily temperature exceeding a certain threshold for a certain minimum amount of time. Various definitions are used in different methodologies for heatwave risk assessments, and in this workflow we will explore the heatwave hazard based on several commonly used methodologies. The risk assessment focuses on the health risks presented to vulnerable population (elderly people).

### Hazard assessment under climate change
To assess the heatwave hazard, we use three different methodologies: EuroHEAT, Peseta IV and Xclim. The user can choose to apply one of these methodologies based on their preferred heatwave definition. The methodologies differ in terms of the required input data, temperature tresholds, duration thresholds, computing algorithm, and results.

 [EuroHEAT](https://climate-adapt.eea.europa.eu/en/metadata/tools/euroheat-online-heatwave-forecast) defines the heatwave as a period where the maximum apparent and the minimum temperature are over the 90th percentile of the monthly distribution for at least two days. The monthly distribution is based on 30-year timeseries of daily temperatures in the recent historical climate (1971-2000).

<span style="color:red">

[Peseta IV](https://joint-research-centre.ec.europa.eu/peseta-projects/jrc-peseta-iv_en) Specifically, a heatwave is defined as a period ≥ 3 consecutive days with a maximum temperature above a daily threshold calculated for a 30-year-long reference period (for testing we choose a shorter period). At least a 30-year time series of daily values is needed to obtain a robust estimation of the indicator. The threshold is defined as the 90th percentile of daily maxima temperature, centered on a 31-day window (we used a month). - how is the threshold calculated?s
</span>

[Xclim](https://xclim.readthedocs.io/en/stable/indicators.html) project defines  a heatwave based on user-defined absolute temperature thresholds for the maximum and minimum daily temperatures (i.e. day and night temperatures), and a mimimum time duration (e.g. 2 or 3 days). Using absolute thresholds for temperature requires input in terms of temperature thresholds, which are typically specific to a region and based on expected health impacts.

Each methodology is demonstrated in this workflow using air temperature data from EURO-CORDEX as input. We use the climate scenarios RCP4.5 (medium) and RCP8.5 (extreme) to compare the effect of different climate scenarios ([more about RCPs](https://en.wikipedia.org/wiki/Representative_Concentration_Pathway)).

As a result of the hazard assessment, we can obtain information about the heatwave frequency of occurrence in the reference period of 1971-2000 and three future periods: 2011-2040, 2041-2070 and 2071-2100. This result is based on model data for climate projections. In all methods yearly frequency of heatwaves is calculated, and monthly frequencies are also calculated in the Peseta IV methodology.

#### Hazard datasets and limitations
Methodologies Peseta IV and Xclim are applied in this workflow based on [EURO-CORDEX data](https://cds.climate.copernicus.eu/cdsapp#!/dataset/projections-cordex-domains-single-levels?tab=form).

Heatwave data prepared by the EuroHEAT project is directly available from the [dedicated dataset](https://cds.climate.copernicus.eu/cdsapp#!/dataset/sis-heat-and-cold-spells?tab=form) on the Copernicus Data Store. This data was also prepared based on EURO-CORDEX data.

All 3 methodologies are based on the EURO-CORDEX climate projections data, the resolution of 12x12 km is not suitable for the cities and smaller areas, the dataset does not take into account e.g. the urban heat-island effect.

#### Other heatwave hazard-related online products

- You can also find other sources of heat-wave-related products available online. This part provides you with a quick overview of other available data
- The biggest difference between data provided online and results provided with this notebook is the resolution of the results, data provided with the Climaax toolbox have more precise resolution than online products. With the Climaax toolbox, you also have the possibility of changing the thresholds that define the heat-wave events (the threshold for temperature and time duration), while the online product has a fixed treshold value

**Copernicus Climate Data store CDS:**

1. **Heat wave days and heat related mortality for nine European cities** (Valencia, Barcelona, Roma, Milan, Munich, Paris, Athens, London Budapest) derived from climate projections [[source](https://cds.climate.copernicus.eu/cdsapp#!/software/app-health-urban-heat-related-mortality-projections?tab=app)]

2. **Heat wave days for Europe derived from ERA5 reanalysis** - NUTS 3 level [[source](https://cds.climate.copernicus.eu/cdsapp#!/software/app-health-heat-waves-current-climate?tab=app)]
    - This application allows users to explore the number of heat waves in European countries based on the ERA5 hourly data on single levels dataset.
A heat wave is a prolonged period of high temperature, relative to the region. A number of qualifying definitions of heat waves are used in the climate and health communities. This application presents two European-wide definitions: the Climatological EURO-CORDEX and Euroheat project , and one set of National definitions which are available for a limited number of European countries.

3. **Heat wave days for European countries derived from climate projections** [[source](https://cds.climate.copernicus.eu/cdsapp#!/software/app-health-heat-waves-projections?tab=app)]
    - This application is an exploratory tool for the Heat waves and cold spells in Europe derived from climate projections dataset. This dataset provides 30 year rolling means of the number of heat wave days based on bias adjusted output from the EURO-CORDEX ensemble of climate models.
A heat wave is a prolonged period of high temperature, relative to the region. A number of qualifying definitions of heat waves are used in the climate and health communities. This application presents two European-wide definitions: the Climatological EURO-CORDEX and Euroheat project , and one set of National definitions which are available for a limited number of European countries.

**Climate adapt**

1. **Heat days occurrence in the past** [[Climate adapt heat days](https://climate-adapt.eea.europa.eu/en/metadata/indicators/high-utci-days)]
2. **Heat days occurrence in the future** [[Climate adapt heat wave](https://climate-adapt.eea.europa.eu/en/metadata/indicators/apparent-temperature-heatwave-days)]
3. **Tropical nights** [[Climate adapt Tropical nights](https://climate-adapt.eea.europa.eu/en/observatory/++aq++metadata/indicators/tropical-nights/)]


### Risk assessment methodology
Under climate change, heatwaves in Europe are expected to occur more frequently. One of the main negative impacts due to heatwaves is the overheating of the urban areas, which lowers the comfort of living and can pose a threat to human health, especially in vulnerable population, but also droughts and water scarcity (see also: [Integrated Assessment of Urban Overheating Impacts on Human Life](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2022EF002682)).

In the risk assessment presented in this workflow, we focus on estimating risk based on population exposure and vulnerability, combined with high-resolution observation data for the temperature (hazard). By combining this assessment with the hazard assessment on changes in future heatwave frequency, it is possible to better estimate the future risks.

As output of the risk assessment, you obtain information about the overheated areas, overlapping with information on the vulnerable population groups. You can also use the vegetation characteristics data to see the influence of the current heat wave events on the vegetation.

We use the 5x5 risk matrix for the risk assessment, which consists of exposure (most exposed places by heat, land surface temperature data) and vulnerability data (vulnerable population groups, world population data). The heat exposure data were divided into 5 groups based on the land surface temperature thresholds (1. Very low <20°C, 2. Low > 20°C, Medium > 30°C, High > 40°C, Very High > 50°C), these thresholds can be changed and values will depend on the selected area (more information in the risk assessment workflow). The vulnerability data were divided into 5 equal interval groups based on the selected area.  

![Heat-wave ilustration](https://github.com/CLIMAAX/HEATWAVES/blob/main/Images/risk_matrix.png?raw=true "Risk matrix example")

#### Risk assessment datasets and limitations

In the risk assessment, we use the information on heat islands based on the [Landsat8 satellite imagery](https://rslab.gr/Landsat_LST.html) to represent the **Exposure**. This dataset estimates the land surface temperature with a spatial resolution of 30x30m for the period 2013-2021. This dataset is available with a 16-day time step. Please note that this is satellite-derived data and some inaccuracy can be caused by missing data on cloudy days.

**Vulnerability** is represented by the WorldPop dataset on vulnerable population groups (people older than 65 and people younger than 5 years old). The spatial resolution of this data is 100x100m. We use the data for the year 2020.


## Structure of the workflow
This workflow consists of several parts, where the user is guided in performing a risk assessment for heat waves. Separate notebooks are available for the three methods of heat wave hazard estimation, followed by the notebook for estimating risk to population and vegetation based on satellite data.

In the next pages you will find:
1. Heatwave hazard assessment using EuroHEAT methodology ([link to notebook on GitHub](https://github.com/CLIMAAX/HEATWAVES/blob/review_edits/heat_wave_hazard_assessment_euroheat.ipynb))
2. Heatwave hazard assessment using Peseta IV methodology ([link to notebook on GitHub](https://github.com/CLIMAAX/HEATWAVES/blob/review_edits/heat_wave_hazard_assessment_pesetaiv.ipynb)
3. Heatwave hazard assessment using Xclim methodology ([link to notebook on GitHub](https://github.com/CLIMAAX/HEATWAVES/blob/review_edits/heat_wave_hazard_assessment_xclim.ipynb)
4. Risk assessment using satellite-derived data ([link to notebook on GitHub](https://github.com/CLIMAAX/HEATWAVES/blob/review_edits/heat_wave_risk_assessment.ipynb))

## Outputs of the workflow

The heatwave hazard workflow gives you the information about the heatwave occurrence in monthly and yearly time steps for the reference period 1971-2000 and projections periods 2011-2040, 2041-2070, and 2071-2100 under two climate scenarios rcps 4.5 and 8.5. This workflow allows you to change the temperature and duration thresholds that specify the heatwave events. You can then discuss which thresholds are best for your area. These results provide you the information on how often you can expect heatwaves in the future. The month's results show the possible seasonal changes in the future (warmer summers or winters?). The duration of the heatwave days is also important to estimate possible heatwave events severity. 

The heatwave risk workflow provides you with information important to estimate which areas are most exposed to the heat, and with the combination of the distribution of the vulnerable groups of the population, you can create a risk map for your selected area. Together with the results of the hazard workflow, you will get comprehensive heat-connected information for present and future climate. 

## Authors of the workflow
This workflow was developed by [KAJO services](https://www.kajoservices.com/). The main contributors to the workflow are:

Martin Kuban, KAJO services.
Milan Kalas, KAJO services.

## References

Euroheat: 11.6.2024 [[source](https://confluence.ecmwf.int/display/CKB/Heat+waves+and+cold+spells+in+Europe+derived+from+climate+projections+documentation#heading-3References)]

Peseta IV: 11.6.2024 [[source](https://cds.climate.copernicus.eu/cdsapp#!/dataset/projections-cordex-domains-single-levels?tab=form)]

XCLIM: 11.6.2024 [[source](https://cds.climate.copernicus.eu/cdsapp#!/dataset/projections-cordex-domains-single-levels?tab=form)]

RSLAB, Land surface Temperature, based on the Landsat8 imagery: 11.6.2024 [[source](https://rslab.gr/Landsat_LST.html)]

<span style="color:red">
Humdata: world population data. Distribution of the critical groups of the population. 11.6.2024 [[source](https://data.humdata.org/dataset/?dataseries_name=Data%20for%20Good%20at%20Meta%20-%20High%20Resolution%20Population%20Density%20Maps%20and%20Demographic%20Estimates&dataseries_name=WorldPop%20-%20Age%20and%20sex%20structures&dataseries_name=WorldPop%20-%20Population%20Density&groups=svk&res_format=GeoTIFF&q=&sort=last_modified%20desc&ext_page_size=25)]
</span>


Copernicus browser: Sentinel2 LA2 imagery for the estimation of the NDVI. 11.6.2024 [[source](https://browser.dataspace.copernicus.eu/?zoom=15&lat=49.19843&lng=18.72718&themeId=DEFAULT-THEME&visualizationUrl=https%3A%2F%2Fsh.dataspace.copernicus.eu%2Fogc%2Fwms%2Fa91f72b5-f393-4320-bc0f-990129bd9e63&datasetId=S2_L2A_CDAS&fromTime=2019-08-31T00%3A00%3A00.000Z&toTime=2019-08-31T23%3A59%3A59.999Z&layerId=1_TRUE_COLOR&demSource3D=%22MAPZEN%22&cloudCoverage=30&dateMode=SINGLE)]

Cropinn: NDVI classes. 11.6.2024 [[source](https://www.cropin.com/blogs/ndvi-normalized-difference-vegetation-index)]

