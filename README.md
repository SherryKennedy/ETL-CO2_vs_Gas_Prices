# Are the trends of CO2 Emissions similar to that of Gas Prices from 1990 to 2020? 
Please refer to the [report](https://docs.google.com/document/d/14F4xUKnnTIMCbx-4Z3-IhaLq061oqAbEGB7vniyEzns/edit?usp=sharing) for a thorough explanation of this project. Below you will find the analysis steps and links to the relevant folders and files.

## Motivation
In 2021, gas prices are on the rise. Additionally, there has been a meeting of COP26, the 26th Conference of the Parties to the United Nations Framework Convention on Climate Change. Canada has confirmed that achieving a net-zero economy by 2050 is required to avoid the worst impacts of climate change. This change will impact industries including the gas / oil industry. 

## Project Objective
### Hypothesis: 
Are the trends of Carbon Dioxide (CO2)  Emissions similar to that of Gas Prices from 1990 to 2020 for Quebec? (British Columbia, Alberta, Ontario not analysed at this time)

### Questions to answer:
* What are the average yearly gas prices for each province stated between 1990 and 2020?
* What are the CO2 emissions for these years?
* Do CO2 emissions have a similar trend compared to gas prices?

To answer these questions, we downloaded CSV files of gas prices, and of CO2 emissions. Ultimately, we had to map the yearly gas prices with the yearly CO2 emissions.

## ETL Analysis Steps

## EXTRACT
### [Gas Prices CSV:](https://github.com/SherryKennedy/ETL-Project/blob/main/Resources/gas_prices.csv)
We filtered through the provided data on the Statistics Canada website for specific provinces, fuel type, as well as the reference time period. The provinces were filtered for; British Columbia, Alberta, Ontario and Quebec, and a timeline of between January 1990 and December 2020. The type of fuel we focused on was Regular unleaded gasoline at self service filling stations. 

Code: [CO2_Data Jupyter Notebook](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)

### [CO2 Emissions CSV:](https://github.com/SherryKennedy/ETL-Project/blob/main/Resources/gas_emissions.csv)
Global data included all countries and many years of CO2 emissions from the burning of fossil fuels. 

Code: [CO2_Data Jupyter Notebook](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)

## TRANSFORM
### [Gas Prices CSV:](https://github.com/SherryKennedy/ETL-Project/blob/main/Resources/gas_prices.csv)
* We filtered through the DataFrame to select particular columns from the CSV
* We cleaned the DataFrame by checking for null values, splitting columns to refine data, extract particular values, dropping unnecessary and ambiguous data, renaming and rearranging the order of columns.
* We finally grouped the data by Year in order to merge data later on.

Code: [CO2_Data Jupyter Notebook](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)

Output: [Data/clean_gas_prices.csv](https://github.com/SherryKennedy/ETL-Project/blob/main/Data/clean_gas_prices.csv)


### [CO2 Emissions CSV:](https://github.com/SherryKennedy/ETL-Project/blob/main/Resources/gas_emissions.csv)
* We filtered for 'Canada' data between 1990 and 2020 specifically
* We cleaned the DataFrame by checking for null values, changing data types, converting values to appropriate units, dropped unnecessary columns and renamed columns.
* We finally grouped the data by Year in order to merge to the previous data set later on.

Code: [CO2_Data Jupyter Notebook](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)

Output: [Data/clean_emissions_data.csv](https://github.com/SherryKennedy/ETL-Project/blob/main/Data/clean_emission_data.csv)

## LOAD
### [Loading Data Locally](https://github.com/SherryKennedy/ETL-Project/blob/main/CO2_data.ipynb)
* After transforming the data, we saved the [cleaned CSV files](https://github.com/SherryKennedy/ETL-Project/tree/main/Data) to prepare for the loading onto our Data Base.

### [Loading Data into MongoDB](https://github.com/SherryKennedy/ETL-Project/blob/main/Data_to_Mongo.ipynb)
* We connected to the localhost
* We created a collection for each set of data
* We then loaded the CSV files onto MongoDB in json format

### [Queries](https://github.com/SherryKennedy/ETL-Project/blob/main/Data_to_Mongo.ipynb)
* We extracted the data from MongoDB as a DataFrame.
* For the gas prices DataFrame, we created seperate DataFrames for each Province (British Columbia, Alberta, Ontario, Quebec).
* We then merged each Province DataFrame together on the 'Year' column.
* We cleaned the merged DataFrames by removing duplicated and unnecessary  columns.
* Once cleaned, we merged the CO2 Emissions DataFrame to the merged provinces DataFrame.
* FIX THIS


We then ran a number of queries (link) in order to obtain the visualization (link) needed

### Findings (Link to the report)

### Conclusion




