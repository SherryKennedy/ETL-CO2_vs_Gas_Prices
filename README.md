Please refer to the report (link) for a thorough explanation of this project. Below you will find the analysis steps and links to the relevant folders and files for each step.

###Motivation
In 2021, gas prices are on the rise. Additionally, there has been a meeting of COP26, the 26th Conference of the Parties to the United Nations Framework Convention on Climate Change. Canada has confirmed that achieving a net-zero economy by 2050 is required to avoid the worst impacts of climate change. This change will impact industries including the gas / oil industry. 

###Project Objective
Hypothesis: Are the trends of Carbon Dioxide (CO2)  Emissions similar to that of Gas Prices from 1990 to 2020 for Quebec? (British Columbia, Alberta, Ontario not analysed at this time)

Questions to answer:
1. What are the average yearly gas prices for each province stated between 1990 and 2020?
2. What are the CO2 emissions for these years?
3. Do CO2 emissions have a similar trend compared to gas prices?

To answer these questions, we downloaded CSV files of gas prices, and of CO2 . Ultimately, we had to map the yearly gas prices with the yearly CO2 emissions.


###Analysis Steps

###EXTRACT
Gas Prices CSV: (link)
We filtered through the provided data on the Statistics Canada website for specific provinces, and a fuel type, as well as the reference time period. The provinces were filtered for; British Columbia, Alberta, Ontario and Quebec, and a timeline of between January 1990 and December 2020. The type of fuel we focused on was Regular unleaded gasoline at self service filling stations. 

Code: CO2_Data (link)
Output: Data/clean_gas_prices.csv (link)

CO2 Emissions CSV:(link)
Global data included all countries and many years of CO2 emissions from the burning of fossil fuels. 

Code: CO2_Data (link)
Output: Data/clean_emissions_data.csv (link)


###TRANSFORM
Gas Prices CSV:
We filtered through the DataFrame for the data needed
We cleaned the DataFrame

CO2 Emissions CSV:
We filtered for Canada data between 1990 and 2020 specifically
We cleaned the DataFrame

Code: CO2_Data

###LOAD
We loaded the clean DataFrames as CSV (link) locally
We loaded the clean CSV files into MongoDB
We then ran a number of queries (link) in order to obtain the visualization (link) needed

###Findings (Link to the report)

###Conclusion




