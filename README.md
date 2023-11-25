# Fianl Project Data Analyst Program Hebrew University of Jerusalem
This project goal is to consult a potential investor regading his investing strategy in short-term rental properties in Washington, United States, based on Python code analysis of Airbnb data.

# Importing relevant Python librarires
In this stage the phollowing relevant Python libraries are imported: Pandas, Numpy, and Matplotlib.

# Reading the data file
In next stage the data file 'listings.csv' into a Panda's DataFrame.

# Removing duplicated rows and non relevant columns
listings_clean = listings.drop_duplicates().drop(columns

# Filtering Missing values
listings_clean_missing_values = listings_clean.dropna()

# Creating a column for the KPI calculation
listings_clean_missing_values_Washington['price'] = listings_clean_missing_values_Washington['price'].replace('\$', '', regex=True).replace('\,', '', regex=True).astype(float)
listings_clean_missing_values_Washington["forecasted_revenue"] = (listings_clean_missing_values_Washington["price"]*(365-listings_clean_missing_values_Washington["availability_365"]))

