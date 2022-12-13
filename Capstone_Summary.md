# Google-Data-Analytics-Course-Capstone
Capstone/Case Study Project for Google Data Analytics Course 

The Google Data Analytics Course on coursera had a case study/capstone project to put the skills and knowledge I learned throughout the course to test.

The prompt was to analyze and gain an insight on a Bellabeat (fitness wristband) product by analyzing a given dataset from Fitbit.

This file is to practice using Github in order to share my thought processes and findings regarding this capstone project.



**Below are the steps I took in order to complete the capstone project**

Firstly, I downloaded the files from https://www.kaggle.com/datasets/arashnic/fitbit (link was given in the capstone project information)
  It was a collection of user data from Fitbit watches, including the file of interest: dailyActivity_merged
  This csv file consisted of various information about a given user at a given date, including steps taken and calories burned
  I chose to work with this file because it seemed to have a lot of information already available in the file, as well as mathematical trends I could analyze
  
Now was the time to decide what program I would be using in order to complete the project. Since this was supposed to be a learning experience, I wanted to challenge
  myself. Since I already had prior experience in Excel, and the most recently covered topic in the Google Course was R Studio Cloud (so it was fresh in my head), I 
  decided to use Google BigQuery and use SQL queries to process the data. Then I would visualize the data through tableau, since this was the software that I felt the
  course didn't teach enough, and so I was least comfortable with it.
  
I went into BigQuery to create a new project. BigQuery auto-generated a name for the project: "cobalt-academy-360720"
  Under the project, I created a dataset: "Case_Study_1" and uploaded the "dailyActivity" table into it through the Create Table function. 
  The table was named "dailyActivity" and the schemda was auto-detected (likely a comma used as a delimtier due to the file being a csv).
  I created a copy of the "dailyActivity" table, since in the real world, I will never manipulate or change the original dataset. This copy was made through the following
  SQL Query:
  
  
  CREATE TABLE cobalt-academy-360720.Case_Study_1.updated_daily_activity AS 
  SELECT 
  *
  FROM 
  cobalt-academy-360720.Case_Study_1.dailyActivity
  
  
  A new table was created under the Case_Study_1 dataset, and this new table would be the one I changed in order to clean the data.
  
  I realized that in the table, multiple instances occured where the "TotalSteps" was 0. Since this is a physically unlikely situation, an assumption was made
  that when the TotalSteps = 0, the watch was likely taken off for the day. Therefore, I decided to delete any rows in the table that had the TotalSteps as 0, since
  I didnt need that data in order to create my insights. The deletion was done through:
  
  
  DELETE FROM 
  cobalt-academy-360720.Case_Study_1.updated_daily_activity
  WHERE
  TotalSteps = 0
  
  
  This deleted numerous rows from the table. I exported this updated table into Google Sheets(because there was no other option with the free version of
  BigQuery) and downloaded as an Excel file.
 
 
**Exporting the data into Google Sheets had created an unnecessary first row of information, including the name of the table and the current date. Since this messed
  with the importing of the data in Tableau, I decided to delete the first row and shift all rows up, so that the first row would be the names of the columns.**
  
  
Now that I had the data of interest as an excel file, I decided to go on Tableau to create a new visualization. 
  Into the Data Source tab, I uploaded the updated_daily_activity.xls file
  I went into a separate Sheet tab to enter the data visualization screen.
  I wanted to see the relationship between steps taken and calories first, to make sure that it aligns with the biological truth that when you walk, calories
  are burned. To do this I dragged the "Total Distance" table to the "Columns" and the "Calories" to the "Rows"
  This created a visualization that showed a positive correlation between the distance travelled and the calories burned. This was good, since that's what you
  want to see.
  Then I dragged the "LightActiveDistance" and the "VeryActiveDistance" into the same "Column" tab to create 3 separate/faceted visualizations. The result
  looked like this:
  ![image](https://user-images.githubusercontent.com/69092102/187102171-c9f3bf7d-53f0-40c6-b094-0450dce51cc3.png)
  
  The insight was that, although more distance travelled meant more calories burned, there was no relationship between if the calories burned with "light active"
  acitivity vs "very active" activity. This meant that instead of advertising or marketing the watch to people into fitness, it could just as easily reach the
  casual audience, who either walks around alot at their work, or prefers walks over intense jogs, etc.

  
  
  

                                                                      
                                                                      
  
  
  
