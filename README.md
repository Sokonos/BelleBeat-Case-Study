# BelleBeat-Case-Study
Track A (2nd option) for Google data analytics capstone project.
# Overview

This is a case study on smart fitness device usage data to find insights that can
be applied to products and marketing strategies in the company Bellebeat.
The case study has 6 main sections, namely: ask, prepare, process, analyze, share, and act.
Each section documents each phase of the data analysis process that I performed in this case study.

# Ask
### <ins>Business Problem</ins>

What is the business problem? In this scenario it is figuring out how consumers use their smart devices, and understaning
how to apply that knowledge to Bellebeat's products and marketing strategy.

### <ins>Business Tasks</ins>

* Find trends in how consumers use their smart fitness devices
* Create recommendations based on the trends for a specific Bellebeat product
* Also, will create recommendations on how to improve Bellebeat's marketing strategy  

# Prepare
### <ins>Data Sources</ins>
Datasets that I used: Fitbit Fitness Tracker Data by Möbius and Wearable Health Performance Data by Pratyush Puri.

### <ins>Links to the Datasets</ins>
 Here are the links for both of the datasets used in this case study: [Fitbit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit/data/), [Wearable Health Device Performance Data](https://www.kaggle.com/datasets/pratyushpuri/wearable-health-devices-performance-analysis)

### <ins>Data Integrity</ins>
* Last Updated:
  + The FitBit dataset shows that it was updated last year (2024), but still only shows data from 2016 on the participants.
  + The Wearable Helath Device Performance dataset was last updated June 24, 2025.
    
* How the datasets were generated:
  + FitBit data was provided by 30 FitBit users who consented to FitBit tracker data being collected on them from March 12, 2016 to May 12, 2016
  + Wearable Health Device Performance data is all synthetic and not from real testing. While the data is not real, it is made to be close to the actual data that would be found on ecommerce sites. It does contain real data on the brand name, product name, product model, and device specifications.
    
* How the Data is Stored:
  + FitBit dataset is stored across multiple csv files. There are two datasets, the first has data from March 12, 2016 to April 11, 2016, and the second spans from April 12, 2016 to May 12, 2016. When combined, the data spans from March 12, 2016 through May 12, 2016. 
  + Wearable Health Device Performance Data is stored in one csv file.
  + First Dataset (FitBit): These files contain data from March 12, 2016 to April 11, 2016 -> <img width="676" height="339" alt="FItBit_csv_files_3 12 16-4 11 16" src="https://github.com/user-attachments/assets/24812a20-2f75-4f9c-bd04-3f80b805284f" />
  + Second Dataset (FitBit): These files cover the rest of the timeframe -> <img width="680" height="565" alt="FitBit_csv_files_4 12 16-5 12 16" src="https://github.com/user-attachments/assets/4aceba73-919e-4367-b334-943dbb66dac0" />
  + Wearable Health Device Performance Dataset -> <img width="664" height="39" alt="Wearable_Health_Device_Performance_Data" src="https://github.com/user-attachments/assets/85aebbf2-e3e2-453a-9fd1-f26bfa63e210" />

* Data Citations
  + A citation to where the data was genereated is provided by FitBit Fitness Tracker Data
  + No citations are present on the Wearable health Device Performance dataset.
    
* Missing Values
  + Present in some of the data files (csv format) from the FitBit data
  + Present in the GPS_Accuracy_Meters field in the Wearable Health Device Performance data

# Process
### <ins>Tools Used</ins>
  Excel was used to inspect and clean both datasets. Also used Google BigQuery to combine and store the cleaned data from the FitBit csv files. Curated a table from the wearable health device performance data using BigQuery. 
### <ins>Cleaning the Data</ins>
Counted the unique number of Ids for the dailyActivity_merged (March-April) file and found a discrepancy. The number of unique Ids was 35, however, the source that I got the data from claimed that only 30 fitbit user's consented to having their data tracked. I am unsure if some of the Ids correspond to the same user.

<img width="1382" height="929" alt="Screenshot 2025-07-29 205737" src="https://github.com/user-attachments/assets/5ef00fb1-2508-46c6-b023-ff2978c46356" />

One explanation is that some of the Ids correspond to the same user, but the user is using a different FitBit device. Some of the files also show 33 instead of 35, so this is also not consistent across the files.

<img width="1020" height="758" alt="ID_inconsistancy" src="https://github.com/user-attachments/assets/36542644-4419-4ccf-b893-d48dae592983" />

Since it can not be ascertained if some of the Ids and corresponding data should be removed, the data will be kept as is. The other coloumns did not have any issues with them. 

In BigQuery a table was made from the [Wearable Health Device Performance Data](https://www.kaggle.com/datasets/pratyushpuri/wearable-health-devices-performance-analysis) with only the columns that were relevant to the analysis. This is the schema of the table and the first couple of rows from it: 

<img width="300" height="550" alt="Screenshot 2025-07-29 224018" src="https://github.com/user-attachments/assets/03f550f2-c50f-4495-b00b-04310407196a" /> <img width="600" height="591" alt="Screenshot 2025-07-29 224854" src="https://github.com/user-attachments/assets/5c305134-8055-4a2b-a7f5-88d324d7e6b5" />

Here is the SQL query that was used to create it ->

<img width="694" height="160" alt="Custom_Table_for_WHDPD" src="https://github.com/user-attachments/assets/8d2e80de-87c6-4be7-b400-7c3a94fd2a1b" />


# Analyze

# Share
```
```
# Act
```
```
