# LSE_DA_NHS_analysis
NHS final assignment project 

Background/context 

The conservative leadership contest announced a policy that would fine £10 for every missed NHS appointment, in response to the mounting resource constraints the NHS are undergoing. 
The NHS hired an external group of data analysts to assess the level of resource utilisation and the cost of missed appointments. As part of a larger team, the report aims to give an overview of the datasets provided, a picture of the services provided by the NHS over the last year, and the number of appointments. 

Analytical approach 

Pandas and numpy library were used for three datasets – national categories, actual duration and appointments by region. Pandas is helpful with large datasets to break down into dataframes to further filter, sort and explore into smaller sections (by rows, columns and even entries). 

The extension Autopep8 was added to Jupyter Notebooks to make sure that all script was corrected to follow PEP8 guidelines. 

To explore the data, dataframes were made first of each of the three data sets before querying the info(), head(), describe() and value_count() to get an outline of the dataset. Missing values were found by using the NaN function. For e.g. the syntax for the actual duration dataframe looked like this: 

“# Making a list of missing value types

ad = pd.read_csv("actual_duration.csv")
missing_values = ["n/a", "na", "--"]

# Check for missing values.

ad = ad[ad.isna().any(axis=1)]

# print missing values
ad.shape”

Output: (0,8)

To drill down into the original dataframe, subsets had to be made to isolate by variable. For example, when wanting to only view the number of appointments for one region (North West London). 

For example: 

“# create a subset of NC based on location
nc_subset = nc.loc[nc['sub_icb_location_name']
                   == 'NHS North West London ICB - W2U3Z']

print(nc_subset)” 

This pulls up all the data specific to that location. 

Visualisation 

For visualisation matplotlib and seaborn were imported. Although Seaborn was exclusively used for visualisations, it relies on matplotlib to be able to plot graphs so both have to be imported. To make displaying graphs easier, IPython.display was also imported. 
Visualisation and insights 
Lineplots were used to visualise the data as they are most useful when handling datetime variables in your datasets, and as such all-context types, service settings and national categories were able to be plotted across a period of a year, using the appointment month and count of appointments columns in the national category file. Because there were continuous dates for a year it made it easier to spot trends over time. 
The interpretations of the visualisation are discussed in more detail in the presentation but an example of a lineplot is below: 
 
It shows how many appointments each hospital professional type take. It would have been more useful if the healthcare professional type was broken down further from ‘Other Practice Staff’, however we can still interpret that GP doctors consistently had more appointments than any other healthcare professional, although there is an interesting converge around Nov 2021 where other professional staff and GP’s have almost the same number of appointments. It could be linked to the distribution of the covid booster around that time, where patients were able to get their vaccination from a nurse, HCA or a GP depending on their medical history. 


Patterns and predictions 

The business question wanted to know whether resources were being sufficiently used under its current capacity, and whether the number of missed appointments were significant. I do not think the current datasets and ability of this analyst was able to answer these bigger questions, however a thorough exploration of the data so far shows a direction for which further diagnostics is needed.

Key insight 1: capacity of resources is heavily dependent on the region of England. North West London had almost 6 times the amount of appointments that Greater Manchester did, suggesting that North West London is more likely to be under constraint, and therefore benefit more from a missing appointment deterrent, than Manchester would. 

Key insight 2: GP appointments are far more frequent than any other type of appointment and should therefore be the focal point of any policy going forward. 

My overall recommendation is that further discovery into the data is needed, and the data structures for the NHS need to be more standardised. There should be a standardised meaning across EMR systems for consultation length so that there is no ambiguity. There also needs to be more granular details on each healthcare professional type, to understand workload and schedules, to relate it back to the appointment data. 
![image](https://user-images.githubusercontent.com/109659382/199223710-b35b875c-8b7a-4478-ae78-b0232312ea7c.png)
