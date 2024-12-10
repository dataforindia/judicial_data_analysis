
The process to create a dataset for analysing cases registered under IPC section 302 is as follows:
 1. For this analysis we are considering cases which registered in 2017 and 2018 and are marked as disposed. Cases which are pending at the time of analysis are not considered.
 2. Filter out all bail cases (where the case type resembles bail, anticipatory bail, etc.) from this set.
 3. Standardise the `judge_designation` indicator which signifies the designation of the judge hearing a case. For this, we categorise the values in these categories: 
    - special
    - Sessions
    - magistrate
    - other
 4. Standardise the `case_type` indicator which signifies the type of case. Filter out all cases types which are of the types mentioned below: 
    - Preliminary Registration Case/General Registered Case
    - Miscellaneous Criminal Petitions/Applications/Transfer Petitions
    - Complaint/Summary/Warrant (Cannot be 302 Case)
    - Criminal Revision/Appeal (Cannot be for 302 Case)
    - Juvenile Case
    - Bail Case
 5. Consider all the valid case types where the `judge_designation` is either sessions or special
 6. Standardise the `purpose_of_hearing` indicator which signifies the purpose of the hearing for each hearing in a case. We categorise the values in these categories: 
    - pre-trial
    - charge
    - trial
    - conviction/acquittal
    - sentencing
 7. Remove cases which don't have neither pre-trial or a trial hearing
 8. Remove cases which only have pre-trial hearings
 9. We sort the hearings by date and remove cases where we see an overlap. An overlap means that we observe a pre-trial hearing after a trial hearing. This could have happened due to a data entry error or the wrong categorisation of a hearing because of missing information about a case.


Note: The [raw data files](https://devdatalab.org/judicial-data#links) published by [DevDataLab](https://devdatalab.org/) were converted to [parquet files](https://parquet.apache.org/) to reduce query run times. The entire analysis was conducted on parquet files and the results were converted to csv files for creating data visualisations.