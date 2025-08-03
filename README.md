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
* Create recommendations based on the trends for a specific Bellebeat product. I have chosen to apply the insights to their product Time (Time is a wellness watch).
* Also, will create recommendations on how to improve Bellebeat's marketing strategy  

# Prepare
### <ins>Data Sources</ins>
Datasets that I used: Fitbit Fitness Tracker Data by Möbius and Wearable Health Performance Data by Pratyush Puri. 

This is a link to the descriptions of each data field in the FitBit dataset -> [Descriptions PDF](https://storage.googleapis.com/kaggle-forum-message-attachments/2787666/20656/fitabasedatadictionary102320.pdf)

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

Since it cannot be ascertained if some of the Ids and corresponding data should be removed, the data will be kept as is. The other coloumns did not have any issues with them. 

In BigQuery I created a table was made from the [Wearable Health Device Performance Data](https://www.kaggle.com/datasets/pratyushpuri/wearable-health-devices-performance-analysis) with only the columns that were relevant to the analysis. This is the schema of the table and the first couple of rows from it: 

<img width="300" height="550" alt="Screenshot 2025-07-29 224018" src="https://github.com/user-attachments/assets/03f550f2-c50f-4495-b00b-04310407196a" /> <img width="600" height="591" alt="Screenshot 2025-07-29 224854" src="https://github.com/user-attachments/assets/5c305134-8055-4a2b-a7f5-88d324d7e6b5" />

Here is the SQL query that was used to create it ->

<img width="694" height="160" alt="Custom_Table_for_WHDPD" src="https://github.com/user-attachments/assets/8d2e80de-87c6-4be7-b400-7c3a94fd2a1b" />

# Analyze
I used Google BigQuery to combine the daily activites csv files into one table; this is so the complete timeframe (3 months) of data is in one place. Here is the SQL query I wrote to do so -> 

<img width="656" height="161" alt="Query_Joing_the_FitBit_Datasets" src="https://github.com/user-attachments/assets/485b5378-7dd8-45ea-8ad5-00e38cd21c8d" />

To find the total intensity and logged total intensity by day, I made the following query:

<img width="547" height="171" alt="Screenshot 2025-08-01 202509" src="https://github.com/user-attachments/assets/3d852aa1-f3e8-4907-92e6-d8a36b6f09fd" />

This was the result 

<img width="536" height="209" alt="Screenshot 2025-08-01 202737" src="https://github.com/user-attachments/assets/f3f8d9ed-0f56-4c54-964c-157224aaeb90" />

We can see that Sunday has a total distance of 919.53 but the logged distance is zero. This suggests that none of the participants (30 participants) logged data on Sunday over the 3 months that the data was collected; this seems unlikely, however, there does not seem to be a good explaination for this. Also, from this query we can see that Tuesday had the most activity (intensity) at 1141.24 and Sunday the least at 919.53. 
When we calculate the ratio of the logged distance to the total distance we see that it is only 2%. This could suggest that only 2% of the activites done by the users was activity they felt should be recorded. It is good to keep in mind that the activity (intensity) is tracked from 0-3 depending on the level of activity detected, so a majority of the activity detected could just be from everyday tasks or going places rather than exercise.

We can incease the granularity to check for what time of day had more activity (intensity). Here is the SQL code:

<img width="740" height="202" alt="image" src="https://github.com/user-attachments/assets/f6ffd98b-732c-436a-94d6-5ff3a338f148" />


Here is the output

<img width="379" height="77" alt="Screenshot 2025-08-03 003839" src="https://github.com/user-attachments/assets/905631f3-d687-4e34-9888-58fc1b70660a" />


We see that there is more activity beeing done in the PM. This is not enough granularity as it does not cover whether it is happening in the afternoon or evening. So, we need to split PM into afternoon and evening, and split AM into night and moring. The intervals for each are as follows: Night 12:00 AM - 4:59 AM, Morning 5:00 AM - 11:59 AM, Afternoon 12:00 PM - 5:59 PM, Evening 6:00 PM - 11:59 PM.

This query does that:

<img width="809" height="217" alt="image" src="https://github.com/user-attachments/assets/6f33f949-272e-4057-859b-a3a55bd85116" />


Output

<img width="381" height="139" alt="image" src="https://github.com/user-attachments/assets/29abe8aa-f0c3-411a-902e-bacec344830b" />

Here we see that the time of day with the highest activity is the afternoon. The time of day with the least amount of activity is at night with a measly 11016.

Now to figure out the amount of calories burned. While this will not be that useful for answering the business task, it is still good to know in conjunction with the rest of the activity data. 
This query will aggregate total calories burned by the day of the week:

<img width="550" height="183" alt="Screenshot 2025-08-02 005226" src="https://github.com/user-attachments/assets/2fd062be-5de0-4bd5-9858-cee97758e62e" />

Output

<img width="405" height="214" alt="Screenshot 2025-08-02 005233" src="https://github.com/user-attachments/assets/34d25ef1-12c7-4a33-8efe-07aeb9913978" />

Here we see that the amount of calories burned per day is roughly the same with little variance.

One trend that would be useful to know is what the FitBit Users tracking preferences are. This can be sone by taking the distinct number of Ids and divide by 30. This is not accurate as some Ids might belong to the same user, but it will give a rough idea of how many users are tracking certain kinds of activites such as intensity and sleep.

This is the query for activity tracking preferences:

<img width="617" height="81" alt="Tracking_Activites" src="https://github.com/user-attachments/assets/1ff59bbe-8d69-4ca2-a381-daaf459a361e" />

Output

<img width="258" height="57" alt="tracking_activites_preferences_outpu" src="https://github.com/user-attachments/assets/12e7d736-78b0-4314-b44c-3c2262ca4324" />

The total was divided by 35 in this case as the number of unique ids surpassed 30, and also because 35 was the number of unique Ids for activity data. If it was divided by 30, the percentage would be greater than 100 percent. While this could still just be interpreted as every user having this tracking preference, it would be best to keep it in the bounds of 0 to 100 percent to be consistent. 

This is the query for sleep tracking preferences:

<img width="503" height="69" alt="SleepTrackingPreferences" src="https://github.com/user-attachments/assets/8a7304e6-706a-4e05-b6cb-2d24d841858f" />

Output

<img width="256" height="60" alt="SleepPreferencesOutput" src="https://github.com/user-attachments/assets/041b8b59-1cc9-41fa-9cc3-a2a78b8b1e7b" />


I wanted to see what the user satisfaction was depending on the amount of connectivity types with smart health devices, so I used the wearable health device performance dataset for this. 

Here is the query:

<img width="620" height="131" alt="Screenshot 2025-08-03 155025" src="https://github.com/user-attachments/assets/605b58cc-5844-4ea9-ba53-06ad73426a97" />

Output

<img width="386" height="132" alt="User_Satisfaction_Rating_Output" src="https://github.com/user-attachments/assets/b2d29f89-3146-496c-9773-ad2287af11be" />


Unsurpisingly we see that the more connection features the device has the higher the satisfaction rating. It is also good to note, however, that the differnce between the highest and lowest rating is not wide. The satisfaction ratings for the entire dataset only span from 6 to 9.5; this range does not give much variance in the first place, and it is probably skewing the results.



# Share
### <ins> DashBoard </ins>

<img width="1869" height="1400" alt="image" src="https://github.com/user-attachments/assets/7c53ed82-a162-4117-bcc6-1bdaf8ba80f6" />



### <ins> Insights </ins>
* Tuesday was the day with the most distance traveled and distance logged
* Only 2% of total distance traveled was logged by the users
* Calories burned by day are similar with slight variance
* Highest percent of activity (intensity) is done in the afternoon at 39%
* Activity was lowest at night, becomes higher in the morning and afternoon, and falls in the evening
* All users had their preferences set to track activity data (steps, intensity, and calories)
* 80% of users had their preferences set to track sleep data
* Sleep records stayed more or less the same throughout the week
* Total sleep hours was also similar throuhout the week; Monday being the only exception as it is on average 100 hours lower than the other days 
* Average hours asleep was in the range from 6 to 7 hours
* The amount of connectivity features had little difference in user satisfaction ratings. 

# Act
### <ins>Recommendations</ins>


