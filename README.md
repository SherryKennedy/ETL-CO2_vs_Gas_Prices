# Are the Trends of CO<sub>2</sub> Emissions Similar to that of Gas Prices from 1990 to 2020? 
Please refer to the [report](https://github.com/SherryKennedy/ETL-Project/blob/main/Analysis/ETL_Project_Report.pdf) and [proposal](https://github.com/SherryKennedy/ETL-Project/blob/main/Analysis/ETL_Project_Proposal.pdf) for a thorough explanation of this project. Below you will find the analysis steps and links to the relevant folders and files.

## Motivation
In 2021, gas prices are on the rise. Additionally, there has been a meeting of COP26, the 26<sup>th</sup> Conference of the Parties to the United Nations Framework Convention on Climate Change. Canada has confirmed that achieving a net-zero economy by 2050 is required to avoid the worst impacts of climate change. This change will impact industries including the gas / oil industry. 

## Project Objective
### Hypothesis: 
Are the trends of Carbon Dioxide (CO<sub>2</sub>)  Emissions similar to that of Gas Prices from 1990 to 2020 for Quebec? (British Columbia, Alberta, Ontario not analysed at this time)

### Questions to answer:
* What are the average yearly gas prices for each province stated between 1990 and 2020?
* What are the CO<sub>2</sub> emissions for these years?
* Do CO<sub>2</sub> emissions have a similar trend compared to gas prices?

To answer these questions, we downloaded CSV files of gas prices, and of CO<sub>2</sub> emissions. Ultimately, we had to map the yearly gas prices with the yearly CO<sub>2</sub> emissions.

## ETL Analysis Steps

## EXTRACT
### [Gas Prices CSV:](https://github.com/SherryKennedy/ETL-Project/blob/main/Resources/gas_prices.csv)
We filtered through the provided data on the Statistics Canada website for specific provinces, fuel type, as well as the reference time period. The provinces were filtered for; British Columbia, Alberta, Ontario and Quebec, and a timeline of between January 1990 and December 2020. The type of fuel we focused on was Regular unleaded gasoline at self service filling stations. 

Code: [CO2_Data Jupyter Notebook](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)

### [CO<sub>2</sub> Emissions CSV:](https://github.com/SherryKennedy/ETL-Project/blob/main/Resources/gas_emissions.csv)
Global data included all countries and many years of CO<sub>2</sub> emissions from the burning of fossil fuels. 

Code: [CO2_Data Jupyter Notebook](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)

## TRANSFORM
### [Gas Prices CSV:](https://github.com/SherryKennedy/ETL-Project/blob/main/Resources/gas_prices.csv)
* We filtered through the DataFrame to select particular columns from the CSV.
* We cleaned the DataFrame by checking for null values, splitting columns to refine data, extract particular values, dropping unnecessary and ambiguous data, renaming and rearranging the order of columns.
* We finally grouped the data by Year in order to merge data later on.

Code: [CO2_Data Jupyter Notebook](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)

Output: [Data/clean_gas_prices.csv](https://github.com/SherryKennedy/ETL-Project/blob/main/Data/clean_gas_prices.csv)


### [CO<sub>2</sub> Emissions CSV:](https://github.com/SherryKennedy/ETL-Project/blob/main/Resources/gas_emissions.csv)
* We filtered for 'Canada' data between 1990 and 2020 specifically.
* We cleaned the DataFrame by checking for null values, changing data types, converting values to appropriate units, dropped unnecessary columns and renamed columns.
* We finally grouped the data by Year in order to merge to the previous data set later on.

Code: [CO2_Data Jupyter Notebook](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)

Output: [Data/clean_emissions_data.csv](https://github.com/SherryKennedy/ETL-Project/blob/main/Data/clean_emission_data.csv)

## LOAD
### [Loading Data Locally](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)
* After transforming the data, we saved the [cleaned CSV files](https://github.com/SherryKennedy/ETL-Project/tree/main/Data) to prepare for the loading onto our Data Base.

### [Loading Data into MongoDB](https://github.com/SherryKennedy/ETL-Project/blob/main/Data_to_Mongo.ipynb)
* We connected to the localhost.
* We created a collection for each set of data.
* We then loaded the CSV files onto MongoDB in json format.

### [Queries](https://github.com/SherryKennedy/ETL-Project/blob/main/Data_to_Mongo.ipynb)
* We extracted the data from MongoDB as a DataFrame.
* For the gas prices DataFrame, we created seperate DataFrames for each Province (British Columbia, Alberta, Ontario, Quebec).
* We then merged each Province DataFrame on the 'Year' column with that of the CO<sub>2</sub> emissions DataFrame.
* We cleaned the merged DataFrames by removing duplicated and unnecessary  columns.
* Once cleaned, we appended all the merged DataFrames into one DataFrame to use for [visualization](https://github.com/SherryKennedy/ETL-Project/tree/main/Images).

Data Used for the visualization: [Clean Project CO2 Data](https://github.com/SherryKennedy/ETL-Project/blob/main/Data/clean_CO2_project_data.csv)

## [Findings](https://github.com/SherryKennedy/ETL-Project/blob/main/Analysis/ETL_Project_Report.pdf)
### Visualization Done:
* [Gas Prices in Cents per L for British Columbia from 1990 - 2020](https://github.com/SherryKennedy/ETL-Project/blob/main/Images/Gas_Prices_BC_1990_2020.png)
* [Gas Prices in Cents per L for Alberta from 1990 - 2020](https://github.com/SherryKennedy/ETL-Project/blob/main/Images/Gas_Prices_Alberta_1990_2020.png)
* [Gas Prices in Cents per L for Ontario from 1990 - 2020](https://github.com/SherryKennedy/ETL-Project/blob/main/Images/Gas_Prices_Ontario_1990_2020.png)
* [Gas Prices in Cents per L for Quebec from 1990 - 2020](https://github.com/SherryKennedy/ETL-Project/blob/main/Images/Gas_Prices_Quebec_1990_2020.png)
* [CO2 Emissions for Canada from 1990 - 2020](https://github.com/SherryKennedy/ETL-Project/blob/main/Images/CO2_Emissions_1990_2020.png)
* [Logarithmic Chart of Quebec Gas Prices from 1990 - 2020](https://github.com/SherryKennedy/ETL-Project/blob/main/Images/Gas_Prices_Quebec_1990_2020_Log_Chart.png)

### [Analysis](https://github.com/SherryKennedy/ETL-Project/tree/main/Analysis):
### 1990-2008 
There is a general upward trend of emission and gas prices. The CO<sub>2</sub> emissions increased more rapidly than the gas prices. This trend makes sense, as yearly gas prices would not exponentially increase, but increases in the demand of fossil fuels, would spike a large increase in CO<sub>2</sub> emissions.
 
### 1998 
Gas prices dipped (prices historically low). There was an adjustment for inflation. Emissions are still trending upward (Generally, more people purchased fuel causing the increase in emissions.)[(1)](https://www.latimes.com/archives/la-xpm-1998-dec-01-mn-49558-story.html)

### 2000-2003 
There is a small downward trend of emission and gas prices. During this period, WTI prices were stable, generally trading in the area of $30 per barrel. Contributing factors included weak economic growth and oil demand following the events of September 11, 2001.[(2)](https://www.cer-rec.gc.ca/en/data-analysis/energy-markets/archive/canadian-energy-pricing-trends-2011/canadian-energy-pricing-trends-2000-2010-energy-facts.pdf)

### 2007-2008 
Upward trend in both gas prices and emissions. This period was characterized by extreme price volatility. Major contributing factors included ongoing significant growth in financial investment in oil; a falling U.S. dollar; growing demand from emerging economies; geopolitical instability; rising finding and development costs; and, slow non-OPEC production growth.[(2)](https://www.cer-rec.gc.ca/en/data-analysis/energy-markets/archive/canadian-energy-pricing-trends-2011/canadian-energy-pricing-trends-2000-2010-energy-facts.pdf)

### 2008-2009 
This sudden decrease of gas prices after the increase from 2007-2008 may have been affected by the global recession that was characterized by broad-based wealth destruction with the collapse of the U.S. housing market, the failure of a number of major financial institutions and the decline in stock markets. Likewise, more people were being economical with fuel consumption, which justifies the decrease in CO<sub>2</sub> emissions.[(2)](https://www.cer-rec.gc.ca/en/data-analysis/energy-markets/archive/canadian-energy-pricing-trends-2011/canadian-energy-pricing-trends-2000-2010-energy-facts.pdf)

### 2009-2010 
Here, there is an increase in gas prices, as the global economy slowly started to improve, and CO<sub>2</sub> emissions similarly started to increase as well.[(2)](https://www.cer-rec.gc.ca/en/data-analysis/energy-markets/archive/canadian-energy-pricing-trends-2011/canadian-energy-pricing-trends-2000-2010-energy-facts.pdf) 

### 2014-2015  
Booming U.S. shale oil production played a significant role in the oil price plunge from mid-2014 to early 2016. The initial drop in oil prices from mid-2014 to early 2015 was primarily driven by supply factors, including booming U.S. oil production, receding geopolitical concerns, and shifting OPEC policies. This partly explains why the oil price plunge failed to provide a subsequent boost to global activity. Generally, the emissions looked to increase slightly, as all of the fuel created would have been purchased.[(3)](https://blogs.worldbank.org/developmenttalk/what-triggered-oil-price-plunge-2014-2016-and-why-it-failed-deliver-economic-impetus-eight-charts)

### 2015-2016 
There was a drop in gas prices and a drop in emissions. However, deteriorating demand prospects played a role , particularly from mid-2015 to early 2016. The dollar was strong. Inventories were huge. The economy was weak. Oil production was growing. Global demand for oil was decreasing. The economies of Europe and developing countries were weakening. Vehicles are becoming more fuel-efficient.[(4)](https://www.investopedia.com/articles/investing/102215/4-reasons-why-price-crude-oil-dropped.asp) The world economy is growing, suggesting a turning point in clean energy development. A hoped for decoupling of economic growth and increased carbon emissions.[(5)](https://insideclimatenews.org/news/07122015/global-carbon-emissions-rising-decades-decline-2015-study-climate-change-paris/)

### 2016-2018 
Increase in gas prices occured as the gas economy leveled as a result of the previous years. Due to the high demand of gasoline, CO<sub>2</sub> emissions were also on a rise.[(6)](https://www.cer-rec.gc.ca/en/data-analysis/energy-markets/market-snapshots/2018/market-snapshot-canadian-gasoline-prices-rise-highest-level-in-over-3-years.html) 

### 2020 
Dip in oil prices overall, emissions went down.  This is the year of the pandemic, prices of gas went down -  a lot of people were ‘locked down’ world-wide. Thus, it makes sense that fewer emissions would follow.[(7)](https://www.ctvnews.ca/autos/gasoline-sales-plunge-to-lowest-level-in-20-years-during-first-year-of-pandemic-1.5611989)


## Conclusion
With the above timeline analysis, one can not predict the future prices of gas and emission values.[(8)](https://www.canadianenergycentre.ca/oil-and-gas-to-lead-us-energy-consumption-to-2050-says-new-forecast/)[(9)](https://www.cnbc.com/2021/04/15/oil-could-plummet-to-10-by-2050-if-paris-climate-goals-are-achieved.html) Generally, as stated above, gas prices were affected by the economy, overall supply, consumer demand, and world news. Currently, it looks like emissions values are similar to the gas prices (use / generation of oil). During 1998 and 2014-2015, there was not a similar trend to gas price and emission value. Gas prices plunged, but emissions went up.  

Tellingly, during 2015-2016 one can see a downward trend on gas prices as the economy was becoming more fuel-efficient (note: dollar was strong and economy was weak). Although, after 2015-2016, the demand for oil increased again. 

## [Appendix](https://github.com/SherryKennedy/ETL-Project/tree/main/Analysis)
* We calculated the differences in Gas Prices and CO<sub>2</sub> Emissions for each year between 1990-2020.

