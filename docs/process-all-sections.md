The process to analyse cases registered under all IPC sections is as follows:
 1. Filter out pending cases from the cases dataset
 2. Aggregate the IPC acts dataset to filter out acts which have less than 100 cases
 3. Remove all cino with multiple entries in the acts file
 4. Add year and case duration from the case dataset. Assign a value of "-999" for all cases with a negative case duration value
 5. Aggregate the data at the level of state, year and section for further analysis. Remove all rows (sections) where the totalCases is less than 100
 6. Format the section variable in the aggregated file so each row is one section. For e.g a row with a section value of x, y will be converted to two rows with value of x and y respectively. All other values in the source row will be the same for both transformed rows.
 7. Aggregate the file again to ensure only one section per row. Calculate average and median duration for each section. Cases with a negative value for case duration are filtered out. 
 8. Create additional variables for ranking as per the total number of cases under each section. The ranks variables are as follows:
    - Overall 
    - Across each year (from 2010-2020)
    - Across each state
    - Across each state each year
   
Note: The [raw data files](https://devdatalab.org/judicial-data#links) published by [DevDataLab](https://devdatalab.org/) were converted to [parquet files](https://parquet.apache.org/) to reduce query run times. The entire analysis was conducted on parquet files and the results were converted to csv files for creating data visualisations.