## HR Analytics-Dashboard

### Dashboard Link : https://app.powerbi.com/groups/me/reports/2ec168c9-d065-4c00-9e91-98a08a749f57/6aad9a609ff3e1362329?experience=power-bi

## Project Objective
Designed a Report for the HR team of a Tech company called Atlas Labs, which wants to monitor key metrics and understand what factors impact employee attrition. This will help them determine what actions must be taken to retain the employees. 

## Process
### Loading and preparing Datasets

We connected 5 CSV (Comma Separated Values) files    and added a prefix “Dim” or “Fact” in each table name, depending on the type of table.

We created a dedicated “Date” table for accurate date and time reporting. 

Then, we reviewed the tables to ensure the columns are correctly formatted as text, numbers, and dates. 

### Building the Data Model
Using the Kimball Model approach, we worked with facts and dimensions tables to build our model.

Our final data model followed the Snowflake Schema. 

The central point of our model was the fact table named “Performance Rating”. This table contains information about employees' yearly reviews and performance ratings.

We worked with multiple dimension tables: Employee, EducationLevel, RatingLevel, SatisfiedLevel, and Date. These tables provided more context to the data – the who, what, when, where, and why.

### Writing DAX Measures
We created many measures for KPI’s and visualization purposes. Some of them are as follows:

TotalEmployeesDate =

CALCULATE([TotalEmployees], USERELATIONSHIP(DimDate[Date],DimEmployee[HireDate]))

LastReviewDate = 

IF( MAX(FactPerformanceRating[ReviewDate]) = BLANK(), "No Review Yet", MAX(FactPerformanceRating[ReviewDate]))

JobStatisfaction = 

CALCULATE(MAX(FactPerformanceRating[JobSatisfaction]), USERELATIONSHIP(FactPerformanceRating[JobSatisfaction], DimSatisfiedLevel[SatisfactionID]))

Attrition Rate = 

DIVIDE([InactiveEmployees],[TotalEmployees],0)

### Dashboard - Overview

![Screenshot 2025-04-23 140433](https://github.com/user-attachments/assets/b96337ec-cd6d-4be0-9561-140ccea9f41a)


### Dashboeard - Demographics

![Screenshot 2025-04-23 140453](https://github.com/user-attachments/assets/4c082451-ada9-4880-a184-4a3e24c73336)


### Dashboard - Performance

![Screenshot 2025-04-23 140508](https://github.com/user-attachments/assets/061b6c5f-df6d-4038-9cba-fa135316c903)


### Dashboard - Attrition

![Screenshot 2025-04-23 140522](https://github.com/user-attachments/assets/6961cbab-655a-404c-a36b-f5e4f96bd95c)


### Insights
-	Atlas Labs has 1470 employees, with approximately 1200 active and 250 inactive.
-	With approximately 800 employees, our technology department is the largest within the organization.
-	We have a team of roughly 270 sales executives.
-	The age range of our employees is from 18 to 51, with a significant 60% falling within the 20-29 age bracket.
-	The ethnic makeup of our workforce includes 58% identified as white.
-	Factors affecting the attrition rate are Frequent travelling and Overtime requirements.
-	A notable spike in employee attrition occurred in 2016 and 2020.
-	We are experiencing a 40 percent attrition rate among our sales representatives, the highest across all job roles.
-	Employees with one year of tenure have the highest attrition rate at 34%.




