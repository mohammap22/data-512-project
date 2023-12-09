# Smoke Estimates and AQI 

## Goals 
The goal of this project was to collect wildfire and AQI data to analyze the effect wildfires have on AQI. 

## Relevant API Documentation

- [EPA Colab File](https://colab.research.google.com/drive/1bxl9qrb_52RocKNGfbZ5znHVqFDMkUzf)
- [Wildfire GEO Approximation](https://colab.research.google.com/drive/1qNI6hji8CvDeBsnLDAhJXvaqf2gcg8UV)
## Requirements
Need Python installed on the system with pandas, json, time, and requests, sklearn, math, collections, and matplotlib installed as libraries. 

## Files

### Data Files (within the Data Directory)
- `gaseous_aqi_data.json`: Contains data related to gaseous AQI indicators from the US EPA, specifically relating to Larimer County.
- `particulate_aqi_data.json`:  Contains data related to particulate AQI indicators from the US EPA, specifically relating to Larimer County
Both of these JSONs are in the same format. Each key pertains to the year, from 1975 to 2023. Here is a sample value for the year 1986 in `particulate_aqi_data.json`: `"1986": {"0001": {"local_site_name": null, "site_address": "200 W. OAK ST.", "state": "Colorado", "county": "Larimer", "city": "Fort Collins", "pollutant_type": {"81102": {"parameter_name": "PM10 Total 0-10um STP", "units_of_measure": "Micrograms/cubic meter (25 C)", "method": "HI-VOL-SA321A - GRAVIMETRIC", "data": {"19860502": [{"sample_duration": "24 HOUR", "observation_count": 1, "arithmetic_mean": 53.0, "aqi": 49}]`. As one can see, we have data on both the exact date and AQI amount. 

### General Files
`Reader.py`: This is a library **not created by me** used to read the USGS wildfire data.
`project.ipynb`: This is the jupyter notebook file that covers loading in the wildfire data, making the visualizations, combining the AQI and Wildfire data, and producing the smoke estimate model. 
`EPA_AQI_DATA_LOAD.ipynb`: This notebook covers how I loaded the AQI data from the EPA

## Known Issues and Special Considerations

1. The wildfire data pulled from the USGS was combined with multiple other datasets, mistakes could be present. 
2. A poor correlation was found between my wildfire severity index and the real AQI measurements. 

## Additional Resources

- [USGS Wildfire Data Source](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)
- [More Information on Wildfire Smoke](https://www.epa.gov/air-quality/wildfires-and-smoke)
