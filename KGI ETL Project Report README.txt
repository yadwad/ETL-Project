KGI and Associates
Data Science Consultants
ETL Project
June 9, 2018
DataBootCamp

Overview

Our team’s goal is to evaluate the impact of certain economic indicators (such as income amounts and employment rates) have on various lifestyle components in the United States of America.  Our first step in this process is to construct model to quantify the relationship between unemployment at health insurance coverage.  
Extract

For the datasets used we took csv files from kaggle (https://www.kaggle.com/). 
We examined data from “The Variability in the Poverty Rate in the US Counties” dataset at https://www.kaggle.com/rrp170330/variability-in-the-poverty-rate-in-the-us-counties/downloads/variability-in-the-poverty-rate-in-the-us-counties.zip/1.  The primary objective of the dataset is to illustrate the variability in the poverty rate in the US counties by means of one or more of independent.  The dataset includes four data tables:
•	Education.xls 3283 x 47
•	PopulationEstimate.xls 3273 x 117
•	PovertyEstimate.xls 3194 x 24
•	Unemployment.xls 3274 x 48

We used the unemployment data table for this model.

Also we examined data from “The Health Insurance Coverage” dataset at https://www.kaggle.com/hhs/health-insurance.  The primary objective of the data set is to identify the health insurance coverage rates before and after the Affordable Care Act.  The dataset includes one data table
•	States.csv 52 x 14

Transform

We downloaded our datasets, cleaned them of any irrelevant columns and dropped duplicates, forming two dataframes: 
•	New_insurance df 51 x 3 
•	New_employment df 50 x 3
The new_insurance dataframe displays uninsured rates for 2010 and 2015. The new_ employment dataframe displays unemployment rates for 2010 and 2015. 
Next, we aggregated the data from both dataframes by performing a panda merge function on the argument (states) column. Further data cleansing was performed by dropping the nan from the new aggregated dataframe.   

Load

An engine was called up and connected to PostGresSQL in order to store our new dataframe into a relational database.  Two SQL queries were performed to confirm that our relational database was functioning properly:
•	SQL query select uninsured 2010 and 2015 416 x 4
•	SQL query select unemployment rates 2010 and 2015 & uninsured rate 2010 and 2015 100 x 6

Limitations

Difficulties were experienced attempting to cleanse a data table with two columns representing the same data elements.  For example, several data tables included the state name (Alabama) and state abbreviation (AL).  We dropped the state abbreviations column which was assigned the column name state. We renamed the state name column which was assigned the name state area to states.  Also, we experienced difficulty with nan representation after the pandas merge function was executed.  Resulting in the need to execute a dropna () function resulting in new dataframe housing cleaned data. 

Future Studies

In future studies we seek to complete the following analysis
•	Illustrate an inversely proportional relationship between education and poverty. (poverty levels decreases as education levels increase) 
•	Illustrate a proportional relationship between unemployment rates and uninsured rates. (uninsured rates decrease and unemployment rates decrease)
•	Illustrate an inversely proportional relationship between education levels and uninsured rates ability. (Uninsured rates decreases as education levels increase)

We will manipulate the data sets by importing the .csv files into Pandas. We will then filter the data sets for relevant statistical information that can be used for our analyses.  We will then join the Data Frames and then export them into .JSON format for publishing into a database.
