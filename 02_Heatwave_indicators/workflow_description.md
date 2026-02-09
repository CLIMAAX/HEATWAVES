# Heatwaves: overheated areas workflow

This workflow is designed to help in exploring the local and regional risks presented by heatwaves, and assessing the impact of climate change on the heatwave hazard.

:::{dropdown} Introduction video

Please note that the introduction video does not reflect the current Handbook structure. Content has been renamed and/or moved.

<figure class="align-center">
  <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/lifpAD0oKCo?si=lkG_-6fXVG_xhIVy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</figure>

:::


## Methodology and data

A heatwave is defined by the maximum and minimum daily temperature exceeding a certain threshold for a certain minimum amount of time. Various definitions are used in different methodologies for heatwave risk assessments, and in this workflow, we will explore the heatwave hazard based on several commonly used methodologies. The risk assessment focuses on the health risks presented to vulnerable populations.


### Open data products for heatwave hazard assessment

There are several applications available online that allow the user to explore heatwave hazards for European regions without the need to perform their own calculations. Below is an overview of such resources. We recommend to explore these resources first, before using the more detailed CLIMAAX workflow.

Resources available from ClimateAdapt provide information on heatwave indicators that are already aggregated to specific locations or regions using a specific methodology:

 - [Heat days occurrence in the past based on the Universal Thermal Comfort Index](https://climate-adapt.eea.europa.eu/en/metadata/indicators/high-utci-days)
 - [Heat days occurrence in the future climate scenarios based on the Apparent Temperature Heatwave Days Index](https://climate-adapt.eea.europa.eu/en/metadata/indicators/apparent-temperature-heatwave-days)
 - [Occurence of tropical nights under future climate scenarios](https://climate-adapt.eea.europa.eu/en/metadata/indicators/tropical-nights)

These data products may not be sufficient for a more detailed assessment. The CLIMAAX workflows allow for greater flexibility in analyzing the data with the possibility of selecting specific definitions of heatwave events (i.e. the thresholds for temperature and time duration) and defining your area of interest.


### Hazard assessment using EURO-CORDEX climate data

In the workflows, we demonstrate how EURO-CORDEX data can be processed to assess heatwave hazard using two different methodologies:

- [**EuroHEAT**](https://climate-adapt.eea.europa.eu/en/metadata/tools/euroheat-online-heatwave-forecast) defines the heatwave as a period where the maximum apparent and the minimum temperature is over the 90th percentile of the monthly distribution for at least two days. The monthly distribution is based on 30-year time series of daily temperatures in the recent historical climate (1971-2000). Heatwave data prepared by the EuroHEAT project is directly available from the [Climate Data Store](https://cds.climate.copernicus.eu/datasets/sis-heat-and-cold-spells?tab=overview).
- The [**xclim**](https://xclim.readthedocs.io/en/stable/indicators.html) project defines a heatwave based on user-defined absolute temperature thresholds for the maximum and minimum daily temperatures (i.e. day and night temperatures), and a minimum time duration (e.g. 2 or 3 days). Using absolute thresholds for temperature requires input in terms of temperature thresholds, which are typically specific to a region and based on expected health impacts. The xclim methodology in this workflow is applied to [EURO-CORDEX data](https://cds.climate.copernicus.eu/datasets/projections-cordex-domains-single-levels?tab=overview).

The user can choose between these methodologies based on their preferred heatwave definition. The methodologies differ in terms of the required input data, temperature thresholds, duration thresholds, computing algorithm, and results. Using the EuroHEAT workflow is recommended because it utilizes data from multiple regional climate models to provide more reliable results, whereas the Xclim workflow relies on only one regional model.

As a result of the hazard assessment, we can obtain information about the heatwave frequency of occurrence in the reference period of 1971-2000 and three future periods: 2011-2040, 2041-2070 and 2071-2100. This result is based on model data for climate projections. We use the climate scenarios RCP4.5 (medium) and RCP8.5 (extreme) to compare the effect of different climate scenarios.

:::{note}
Both methodologies are based on EURO-CORDEX climate projections. The resolution of this data is approximately 12 × 12km, and therefore it is not suitable for accurately evaluating heat wave risks inside cities, because the dataset does not take into account the urban heat-island effect.
:::


### Risk assessment at the regional level

The results of this workflow provide insights into the relative changes in heatwave occurrence based on the EuroHEAT climate projections data, the distribution of vulnerable population groups ([WorldPop](https://dx.doi.org/10.5258/SOTON/WP00646)), and the projected heatwave risk for these vulnerable groups.

These findings help to better understand the projected magnitude of change in heatwave occurrence and highlight areas with a higher concentration of vulnerable population groups. Additionally, this workflow demonstrates the methodology for combining these two sets of information using a 10 × 10 risk matrix ({numref}`fig-heatwave-10by10-risk-matrix`).

:::{figure} ../images/risk_matrix_10to10.png
:name: fig-heatwave-10by10-risk-matrix

Risk matrix example
:::

It is important to note that the level of risk is dependent on the area selected at the beginning of the analysis. This means that the risk level only reflects differences between the chosen regions.


## Structure of the workflow

This workflow consists of several parts, where the user is guided in performing a risk assessment for heat waves. Separate notebooks are available for the two methods of heat wave hazard estimation, followed by a notebook for estimating the level of risk to the population based on the EuroHEAT data (regional level).

1. [Heatwave hazard assessment: EuroHEAT methodology](./hazard_assessment_euroheat.ipynb)
2. [Heatwave hazard assessment: Xclim methodology](./hazard_assessment_xclim.ipynb)
3. [Risk assessment: vulnerable population](./risk_assessment_population.ipynb)


## Outputs of the workflow

The heatwave **hazard** workflow gives you the information about the heatwave occurrence at a yearly temporal resolution, with the reference period of 1971-2000 and future periods of 2011-2040, 2041-2070, and 2071-2100 under two climate scenarios: RCP4.5 and RCP8.5. This workflow allows you to modify the temperature and duration thresholds that specify the heatwave events according to your needs, you can define which thresholds are best suited for your region. The results provide you the information on how often you can expect heatwaves in the future. The duration of the heatwaves (in days) is also important to estimate possible heatwave events severity. 

The risk assessment at the regional level provides information about the projected heatwave occurrence changes for the near and further future with the combination of the distribution of the vulnerable groups at the regional level. 


## Authors of the workflow

This workflow was developed by [KAJO services](https://www.kajoservices.com/). The main contributors to the workflow are:

- Martin Kuban, KAJO services.
- Milan Kalas, KAJO services.
- Natalia Aleksandrova, Deltares.
