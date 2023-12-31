
# Larimer County Wildfire Smoke Impact Analysis on Population Health
## Overview
This project aims to analyze the relationship between wildfire smoke and respiratory mortality in Larimer County CO. This project is broken down by a handful of notebook files written in Python, which illustrate the data acquisition, analysis, and model creation. This project is split up into two major sections: 1) Proving that US citizens do not care about wildfire smoke. And 2) How wildfire smoke affects respiratory health. Section 1 is contained within `home_price_and_smoke` (data sourced from `load_Census_house_data`) while section two is contained within `mortality_estimation`, which piggybacks off the notebooks contained in the directory `smoke_estimated_and_AQI`.  

## Breakdown of Individual Python Notebooks
1. `home_price_and_smoke`: This notebook explores the relationship between historic median house prices and wildfire smoke.
2. `mortality_estimation`: This notebook uses the estimated smoke severity value (created in `smoke_estimates_and_AQI/creating_smoke_estimate`) and the yearly mortality data, to predict future respiratory mortalities in the Front Range of Colorado.
3. `load_Census_house_data`: uses the US Census API to collect yearly median house prices in the US. 

## Data Acquisition
There are numerous sources of data used in this project:
1. Historic Wildfire Dataset created by the USGS: [source](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)
2. US Census Data for Median Household values: [source](https://www.census.gov/data/developers/data-sets.html)
3. Yearly mortality data for the Front Range of Colorado: [source](https://www.sciencedirect.com/science/article/pii/S0013935123003833)
4. County-wise wildfire smoke levels in the US: [source](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/CTWGWE)
5. US EPA AQI levels: [further information](https://aqs.epa.gov/aqsweb/documents/data_api.html)

### Data Structures
Below is a breakdown of the primary (used) features of the 5 main sources of data:
1. `Historic Wildfire Dataset`: Large GEOJson fire where each object contains information on the fire year (string), type (list of strings), size of the burned region (integer), and boundary of the fire (list of coordinates).
2. `US Census Data`: Large CSV where each row contains MedianHouseValue (integer), State (String), County (String)
3.  `Mortality Data`: Small data frame where each row contains All Causes (int), CVD (int), Respiratory (int), Despair (int), Covid-19 (int)
4.  `County-Wise Smoke Estimations`: Large CSV containing State (fips integer), County (fips integer), low (integer), medium (integer), heavy (integer), Year (integer)
5.  `US EPA AQI`: Large JSON object containing Year (int), Pollutant Type (string), aqi (int)

## Data Processing
Each Python notebook file includes code on how to load or create used data sources. Two datasets need to be downloaded as CSVs, those are numbers 1 and 4 in the `Data Acquisition` section. You can download these CSV files using the links provided. 

## Requirements
Python 3.x, matplotlib, NumPy, Requests, defaultdict, and Pandas, time, shapely, re, and collections

## License and Terms of Use
The data is sourced from Wikipedia under the Wikimedia Foundation's terms. Please review the Wikimedia Foundation REST API [terms of use](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions) for more details.

## API Documentation
As mentioned previously, the EPA and US Census APIs were used, here are the links to their information pages:
1. [EPA](https://aqs.epa.gov/aqsweb/documents/data_api.html)
2. [US Census](https://www.census.gov/data/developers/guidance/api-user-guide.html)


## Known Issues and Special Considerations
The created smoke estimation values are based upon historic wildfire data which only contain the size, year, and location of the fire. Thus we are missing wind data, which is very important when trying to track wildfire smoke. The mortality data is sourced from mortality data in the Front Range of Colorado, while we are only looking at Larimer County, which is only a portion of the Front Range. 

## Running the Code
Download datasets 1 and 4. Move the historic smoke data (dataset 1) into the `smoke_estimates_and_AQI` directory. Create a subdirectory called `smoke_data` and move the county-wise smoke data into the `smoke_data` directory. After downloading the necessary libraries mentioned in the `Requirements` section, incrementally run either `mortality_estimation` or `home_price_and_smoke` to view results. 
