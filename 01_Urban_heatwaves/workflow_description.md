# Workflow for heatwave risk assessment under climate scenarios

A heatwave is a prolonged period of abnormally hot weather. There are different approaches to defining a heatwave. But in general, a heatwave is determined using thresholds for air temperature and its persistency (minimum duration as a number of days). The most common definition of a heatwave is the occurrence of multiple consecutive days with the maximum air temperature over a certain threshold. In some methodologies thresholds are also defined for the minimum air temperature.

The heatwave workflow focuses on estimating the frequency of heatwave events for the present and the future climate based on the EURO-CORDEX climate scenarios data (dataset with 12 km spatial resolution). The workflow aids the user in understanding the effect of climate change on the occurrence of heatwaves under different climate change scenarios (RCPs) within a user-defined region in Europe. This data is obtained for yearly temporal resolutions. Changes to heatwave duration (total number of days) are also analyzed. This workflow also includes an analysis of the relative change in heatwave occurrence at the regional level. It provides a methodology for combining the magnitude of this relative change with data on vulnerable populations. 

The risk to the vulnerable population due to heatwaves can be analyzed using the heatwave hazard data in combination with the information on the distribution of the vulnerable population groups. In this workflow, we demonstrate such analysis using high-resolution satellite-derived (measured) data on heatwaves (30m spatial resolution) with the combination of the distribution of the vulnerable groups (100m spatial resolution). In this workflow, you will find instructions on where to find these data and how to analyze this information. 


## Risk assessment methodology based on historical high-resolution data

One of the main negative impacts of heatwaves is the overheating of the urban areas, which lowers the comfort of living and can pose a threat to human health, especially in vulnerable populations, but also droughts and water scarcity (see also: [Integrated Assessment of Urban Overheating Impacts on Human Life](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2022EF002682)).

In the risk assessment example presented in this workflow, we focus on estimating risk based on population exposure and vulnerability, combined with high-resolution observation data for the temperature (hazard). By combining this assessment with the hazard assessment on changes in future heatwave frequency, it is possible to better estimate the future risks.

As output of the risk assessment, you obtain information about the overheated areas, overlapping with information on the vulnerable population groups. 

To assess risk, we use a 10+10 risk matrix, which consists of exposure (level of exposure to heat based on land surface temperature data) and vulnerability (vulnerable population groups based on world population data). The heat exposure data were divided into 10 groups based on the land surface temperature thresholds (1-2. Very low <20-25°C, 3-4. Low 25-35°C, 5-6. Medium 35-45°C, 7-8. High 45-55°C, 9-10. Very High 55-60<°C), these thresholds can be changed and values will depend on the selected area (more information in the risk assessment workflow). The vulnerability data were divided into 10 equally-spaced intervals based on the selected area.  

![heatwave ilustration](../images/risk_matrix_10to10.png "Risk matrix example")


## Risk assessment datasets and limitations

In the risk assessment, we use the information on heat islands based on the [Landsat8 satellite imagery](https://rslab.gr/Landsat_LST.html) to represent **exposure**. This dataset estimates the land surface temperature with a spatial resolution of 30x30m for the period 2013-2021. This dataset is available with a 16-day time step. Please note that this is satellite-derived data and some inaccuracy can be caused by missing data on cloudy days.

**Vulnerability** is represented by the WorldPop dataset on vulnerable population groups (people older than 65 and people younger than 5 years old). The spatial resolution of this data is 100x100m. We use the data for the year 2020.


## Structure of the workflow

1. [Hazard assessment using satellite-derived data](hazard_assessment.ipynb)
1. [Risk assessment using satellite-derived data](risk_assessment.ipynb)


## Outputs of the workflow

The heatwave **risk** workflow provides you with information important to estimate which areas in your region are most exposed to the heat. By combining this with the distribution of vulnerable groups of the population, you can create a risk map for your selected area. Together with the results of the hazard workflow, you will get information both on the future heatwave hazard and the areas most exposed to this hazard under the current and future climate.


## Authors of the workflow

This workflow was developed by [KAJO services](https://www.kajoservices.com/). The main contributors to the workflow are:

- Martin Kuban, KAJO services.
- Milan Kalas, KAJO services.
- Natalia Aleksandrova, Deltares.


## References

- RSLAB, Land surface Temperature, based on the Landsat8 imagery: 11.6.2024 [[source](https://rslab.gr/Landsat_LST.html)]
- Humdata: world population data. Distribution of the critical groups of the population. 11.6.2024 [source](https://dx.doi.org/10.5258/SOTON/WP00646)
