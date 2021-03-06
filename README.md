# **Introduction**

This is a case study for Google Data Analytics Professional. In this study, I am going to analyse a public dataset for the marketing department of Bellabeat, a brand providing products and services for women's health.

**About the company**

Bellabeat develops wearable products to monitor daily habits and collect lifestyle data, to help women more understand their bodies through those data, hence making a better choice. The main products are Leaf, Time, Spring, Bellabeat App. In this case study, I will focus on Leaf, a wearable device tracking daily activities like sleeping duration and calories burned.

**Stakeholders**

*Internal:*

-Urška Sršen: Bellabeat’s co founder and Chief Creative Officer

-Sando Mur: Bellabeat’s co founder and key member of the Bellabeat executive team

-Marketing team of Bellabeat

*External:*

-Bellabeat’s client

-Bellabeat’s future client

**Data**

The public dataset (FitBit Fitness Tracker Data)[1] is used for this study. This dataset was provided by Google and was generated by respondents to a distributed survey via Amazon Mechanical Turk between 12/04/2016 - 12/05/2016.

# **(1)Ask**
​
The 3 main questions of this project:

1. How does daily workout affect calories burned?

2. How does daily workout affect sleeping quality?

3. How to attract more people to use our products?
​
# **(2)Prepare**
​
Data content: 18 tables, tracking users' calories, daily steps taken, active minutes, sleeping time, weight, etc…

Sample size: Maximum 33

Time frame: 12/04/2016 - 12/05/2016
​

**(2.1)Choose data and software**


Spreadsheet is used for data cleansing, MySQL for generating the data for visualisation, and Tableau for the visualisation.

To answer the 3 questions in ASK PHASE, I chose 4 tables for this project: 
dailyActivity_merged
hourlyIntensities_merged
sleepDay_merged
weightLogInfo_merged
​
First, have a preview of what we get, find the number of distinct id for the tables:

select count(distinct id)
from dailyActivity_merged

select count(distinct id)
from hourlyIntensities_merged_merged

select count(distinct id)
from sleepDay_merged_merged_merged

select count(distinct id)
from weightLogInfo_merged

33

33

24

8

As you can see, there is a big variance of IDs between tables, only 72% of respondents recorded their sleeping and 24% recorded their weight info. Since there is such a big difference thus the data is not reliable, so I was not using the weight info.


**(2.2)Cleaning data**

-Trim space

-Delete duplicate

-Transform date: Dates in different table have different presentation, therefore change all to dd/mm/yyyy

-Delete time and am/pm: Since the data would be analysed day-based, time is irrelevant in this project.


# **(3,4)Process and Analyse**

Then, to answer the question in Phase1, I want to know which parameters burn the most calories. Workout duration? Total steps are taken? Or total distance walked?

select id, activitydate, totalsteps, totaldistance, 
VeryActiveMinutes + FairlyActiveMinutes + lightlyactiveminutes AS activeminutes,
calories
from dailyactivity

