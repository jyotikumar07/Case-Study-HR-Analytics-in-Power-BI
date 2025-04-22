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

![Image](https://github.com/user-attachments/assets/3af84d57-5acd-45fb-b535-e55bb2277bcb)

### Dashboeard - Demographics

![Demographics](https://github.com/user-attachments/assets/a958453f-5631-4b68-b50d-626e2cfdac10)

### Dashboard - Performance

![Performance Tracker](https://github.com/user-attachments/assets/153cbfa8-33d0-42b0-9ff0-84adef7fc31a)

### Dashboard - Attrition

![Attrition](https://github.com/user-attachments/assets/21377b4c-56b4-4c1d-8e25-1636dbc9999c)



