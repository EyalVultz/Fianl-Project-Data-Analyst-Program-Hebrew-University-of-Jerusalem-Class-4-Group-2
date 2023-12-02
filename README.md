# Fianl Project Data Analyst Program Hebrew University of Jerusalem Class 4 Group 2

## Table of Contents
- [Project Overview](#Project-Overview)
- [Data Sources](#Data-Sources)
- [Tools](#Tools)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Data Analysis](#Data-Analysis)
- [Recommendation](#Recommendation)



## Project Overview
This project goal was to consult a potential investor regading his investing strategy in short-term rental properties in Washington, United States. 


## Data Sources
 - 'listing.csv' - Airbnb data file.
 - 'Inside Airbnb Data Dictionary.csv' - Table which contains indication of each field (column) type and a short explanation.


## Tools
- Microsoft Excel - Primary data overview.
- Python (Jupyter Notebook) - Data Analysis and Visualization (graphs).
- Microsoft PowerPoint - Reporting. 


## Exploratory Data Analysis
The Exploratory Data Analysis (EDA) of this projects includes answering the following questions:
1. What is the Type of the Properties with the highest Forecasted Coming Year Revenue in Washington, United States?
2. In which Neighbourhood in Washington, United States are located the Properties with the highest Forecasted Coming Year Revenue?
3. What is the Room Type of the Properties with the highest Forecasted Coming Year Revenue in Washington, United States?
4. What is the number of Accommodates of the Properties with the highest Forecasted Coming Year Revenue in Washington, United States?


## Data Analysis
The Data Ananlysis contained the following Stages:

### Stage 1: Importing relevant Python libraries
In this stage the relevant Python libraries, Pandas, Numpy, and Matplotlib, were imported.

### Stage 2: Reading the data file
This stage includes the data file 'listings.csv' reading into listings, a Panda's DataFrame.

### Stage 3: Data cleaning
listings was filtered in this stage from duplicated records (rows) by the drop_duplicates() method and from irrelevant fileds (columns) by the drop() method
to a new DataFrame, listings_clean. It should be indicated that with the 'bedrooms' and 'beds' fileds the dropna() method resulted in loosing of ~44% of the 
records, while filtering thoese fileds out resulted in loosing just loosing ~27% with the of the records by the last method. This was due to 'neighbourhood' field
keeping, which was found essential for assuring that the properties are located indeed in Washington and as described in the next paragraph. 
The listings_clean Dataframe was cleaned then from rows containing Missing Values by the dropna() method to a new DataFrame, listings_clean_missing_values. 

### Stage 4: Filtering out properties (rows) not located in Washington
In this stage listings_clean_missing_values was cleaned from properties (rows) which are not located in Washington, based on the 'neighbourhood' field (column),
while forming a new DataFrame, listings_clean_missing_values_Washington.

### Stage 5: Creating a new column for the KPI calculation
The KPI which was chosen was the propertirs with the Coming Year Forecasted Revenue, which is the most important issue for an investor, in the abscence of the
properties' acqusition price data. The use of an annual data aims to eliminate the phenomenon of price seasonality of each property. 
The Forecasted Revenue in the Coming year for each property was calculated by multiplying the 'price' field (column) by the diffrence between 365 (days) and the
'availability_365' field (column), while the last difference result gives the forecasted number of days in which a givven property is forecasted to be rented in 
the coming year, resulting in a Revenue formation for its host, and as follow:
'price' * (365 - 'availability_365').
These calculations' results formed a new column named 'forecasted revenue' in the DataFrame listings_clean_missing_values_Washington. 
Prior to the formation of the above KPI column it was needed to convert the 'price' field (column) variable type from currency to float.

### Stage 6 - Route A: Trial to Characterize the Top 25% (Q1) properties by their Coming Year Forecasted Revenue
listings_clean_missing_values_Washington DataFrame was analyzed then by the describe() method, resulting in that the Top 25% (Q1) of the properties in Washington, 
United States were forecasted to gain in the coming year between 49,728 USD to 2,190,000 USD, Q2 between 29,186 USD to 49,727 USD, Q3 between 11,784 USD to
29,185 USD and Q4 from 0 to 11,783 USD. listings_clean_missing_values_Washington DataFrame was filtered then according to the above by the query() method, 
while forming 4 new Dataframes named: listings_clean_missing_values_Washington_Q1, listings_clean_missing_values_Washington_Q2, 
listings_clean_missing_values_Washington_Q3. and listings_clean_missing_values_Washington_Q4.

![image](https://github.com/EyalVultz/Fianl-Project-Data-Analyst-Program-Hebrew-University-of-Jerusalem/assets/151207530/c1c5ff65-a1cd-4de0-9276-405532d89ab9)

### Stage 7 - Routh A: Analyzing the properties' by Coming year Forecasted Revenue Quarterials in Washington, United States, by their Property Type
Analyzing the properties' by Coming year Forecasted Revenue Quarterials in Washington, United States, by their Property Type was performed in this stage, while using
the value_counts() method, followed by evaluation of the results by a Bar graph by using the the plot() method for each one of the above 4 DataFrames. 
This revealed that significantly the most common Type of the properties in the above Q1, Q2, and Q3 most common type was Entire Home. 
listings_clean_missing_values_Washington_Q1, listings_clean_missing_values_Washington_Q2, and listings_clean_missing_values_Washington_Q3 DataFrames were filtered
then according to the above by the str.contains() method, while forming 3 new Dataframe named listings_clean_missing_values_Washington_Q1_Entire_home,
listings_clean_missing_values_Washington_Q2_Entire_home, and listings_clean_missing_values_Washington_Q3_Entire_home

### Stage 7: Further Filtration by Neighbourhood and then by Room Type
Trying to further specify the above Q1 properties by their Neighbourhood revealed that all of them are located in Seattle, and their Room Type is Entire home/apt.

### Stage 8: Final Filtration by Accommodates Number
Analyzing listings_clean_missing_values_Washington_Q1_Entire_home DataFrame by the number of Accommodates, while using the value_counts() method followed by 
evaluating the results by a Bar graph using the the plot() method, revealed that the these properties significantly most common number of Accommodates is 6 people.



## Recommendation
Following the above Data Analysis it can be recommended to the potential investor to purchase properties in Washington, United States which are Entire Home by
type, located in Seattle, which their room type is Entire Home / Apartment, and which are suitable to accommodate 6 people, as these properties are forcasted to
gain the higest revenue in the coming year.
