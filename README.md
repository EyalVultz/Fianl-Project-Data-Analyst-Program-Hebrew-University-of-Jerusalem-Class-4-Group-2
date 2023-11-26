# Fianl Project Data Analyst Program Hebrew University of Jerusalem

## Project Overview
This project goal was to consult a potential investor regading his investing strategy in short-term rental properties in Washington, United States. 


## Data Sources
 - 'listing.csv' - Airbnb data file.
 - 'Inside Airbnb Data Dictionary.csv' - Table which contains indication of each field (column) type and a short explanation.


## Tools
- Microsoft Excel - Primary data overview.
- Python (Jupyter Notebook) - Data Analysis and Visualization (graphs).
- Microsoft PowerPoint - Reporting. 


## Data Analysis
The Data Ananlysis contained the following Stages:

### Stage 1: Importing relevant Python libraries
In this stage the relevant Python libraries, Pandas, Numpy, and Matplotlib, are imported.

### Stage 2: Reading the data file
This stage includes the data file 'listings.csv' reading into listings, a Panda's DataFrame.

### Stage 3: Data cleaning
listings is filtered in this stage from duplicated records (rows) by the drop_duplicates() method and from irrelevant fileds (columns) by the drop () method
to a new DataFrame, listings_clean. This Dataframe is cleaned from rows containing Missing values by the dropna() method to a new DataFrame, 
listings_clean_missing_values.

### Stage 4: Filtering out properties (rows) not located in Washington
In this stage listings_clean_missing_values is cleaned from properties (rows) which are not located in Washington based on the 'neighbourhood' field and form a new 
DataFrame, listings_clean_missing_values_Washington.

### Stage 5: Creating a new column for the KPI calculation
The KPI which I have chosen to use is the Top 25% (Q1) propertirs according to thier Forecasted Revenue in the Coming year, which is the most important issue for
an investor, in the abscence of the properties'
purchasing price data, while using an annual data can eliminate the price seasonality phenomenon of each property. 
The Forecasted Revenue in the Coming year for each property is calculated by multiplying the 'price' field (column) by the diffrence between 365 (days) and the
'availability_365' field (column), while the 
last difference result gives the forecasted number of days in which a givven property is forecasted to be rented in the coming year, resulting in a Revenue 
formation for its host, and as follow:
'price' * (365 - 'availability_365')
These calculations' results form a new column named 'forecasted revenue' in the DataFrame listings_clean_missing_values_Washington. 
Prior to the formation of the abpve KPI column it was needed to convert the 'price' field (column) variable type from currency to float.
listings_clean_missing_values_Washington DataFrame is analyzed then by the describe() method resulting in that the Top 25% (Q1) of the properties in Washington, 
United States are forecasted to gain
in the coming year between 55,927 USD to 2,190,000 USD.
listings_clean_missing_values_Washington DataFrame is filtered then according to the above by the query() method, while forming a new Dataframe named 
listings_clean_missing_values_Washington_Q1.

### Stage 6: Analyzing Top 25% properties in Washington, United States by Coming year Forecasted Revenue, by their Property Type
Analyzing Top 25% properties in Washington, United States by Coming year Forecasted Revenue by Property Type is performed in this stage, while using the
value_counts() method, followed by evaluating the results by a Bar graph using the the plot() method, reveals that the these properties significantly most 
common type is Entire Home. listings_clean_missing_values_Washington_Q1 DataFrame is filtered then according to the above by the str.contains() method, while
forming a new Dataframe named listings_clean_missing_values_Washington_Q1_Entire_home. 

### Stage 7: Further Filtration by Neighbourhood and then by Room Type
Trying to further specify the above Q1 properties by their Neighbourhood revealed that all of them are located in Seattle, and their Room Type is Entire home/apt.

### Stage 8: Final Filtration by Accommodates Number
Analyzing listings_clean_missing_values_Washington_Q1_Entire_home DataFrame by the number of Accommodates, while using the value_counts() method followed by 
evaluating the results by a Bar graph using the the plot() method, reveals that the these properties significantly most common number of Accommodates is 6 people.


## Conclusion
Following the above Data Analysis it can be recommended to the potential investor to purchase properties in Washington, United States which are Entire Home by
type, located in Seattle, which their room type is Entire Home / Apartment, and which are suitable to accommodate 6 people, as these properties are forcasted to
gain the higest revenue in the coming year.
