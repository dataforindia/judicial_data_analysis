
The process to analyse cases registered under all acts is as follows:
 1. Filter out pending cases from the cases dataset
 2. Filter out unwanted/unclear act names. Check the [unclear_act_names](resources/unclear_act_names.md) file for details.
 3. Aggregate the state acts file to filter out acts which have less than 500 cases
 4. Merge the acts file with the case details file to get the year value for cases 
 5. Ensure that all cino have only one unique year value. Filter the cino's which have more than one value for the year variable
 6. Get date of registration and decision from the case dataset. Calculate the duration of cases in terms of number of days
 7. Assign a value of `-999` to cases which have a negative case duration value
 8. Merge all the state level act files into a single file.
 9. Format (convert to lower case and remove extra spaces) all act names.
 10. Standardise the acts as per the mappings mentioned [here](resources/group_of_acts/)
 11. Aggregate the act file to calculate total number of cases, mean and median duration of cases for each act, state, year. In this step, cases with a negative duration value are not considered for further analysis. Acts with less than 100 cases for each state and year are removed from the dataset.
 12. Create additional variables for ranking as per the total number of cases under each act. The ranks variables are as follows:
    1. Overall 
    2. Across each year (from 2010-2020)
    3. Across each state
    4. Across each state each year
   
Note: The [raw data files](https://devdatalab.org/judicial-data#links) published by [DevDataLab](https://devdatalab.org/) were converted to [parquet files](https://parquet.apache.org/) to reduce query run times. The entire analysis was conducted on parquet files and the results were converted to csv files for creating data visualisations.