# Fianl Project Data Analyst Program Hebrew University of Jerusalem
This project goal is to consult a potential investor regading his investing strategy in short-term rental properties in Washington, United States, based on Python code analysis of Airbnb datafile.

# Importing relevant Python librarires
In this stage the relevant Python libraries, Pandas, Numpy, and Matplotlib, are imported.

# Reading the data file
This tage includes the data file 'listings.csv' reading into listings, a Panda's DataFrame.

# Data cleaning
The DataFrame is filtered from duplicated records (rows) by the drop_duplicates() method and from irrelevant fileds (columns) to the into a new DataFrame, listings_clean. 

# Filtering Missing values
listings_clean_missing_values = listings_clean.dropna()

# Creating a column for the KPI calculation
listings_clean_missing_values_Washington['price'] = listings_clean_missing_values_Washington['price'].replace('\$', '', regex=True).replace('\,', '', regex=True).astype(float)
listings_clean_missing_values_Washington["forecasted_revenue"] = (listings_clean_missing_values_Washington["price"]*(365-listings_clean_missing_values_Washington["availability_365"]))

# Conclusion
The recommendation to the potential investor in properties next year in Washington, United States, based on the above Data Analysis, is for Entire Home type properties, located in Seattle, which their room type is
Entire Home / Apartment, and which are suitable to accommodate 6 people.
