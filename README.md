# Bellabeat_fitness
Analysis of the trend and pattern of Bella Beat fitness for women
This analysis is designed to study the trends and patterns of the users of Bellabeat fitness products, to know how the products can serve them better and bring out the best in their health. Hence, advise the Bella beat board on how to implement the discovery.

The project will be segmented as follows:
### ASK

### PREPARE

### PROCESS

### ANALYSE

### SHARE 

### ACT.

# Step 1: ASK

The challenges and objectives of the case study will be provided in this first (ask) step, followed by the needed outcome. This will give us clarity to work on the rest of the steps.
**Brief Background**

Bellabeat is a high-technological producer of smart health-induced products for women; this is aimed at providing a healthy and physically fit life style for women. Bellabeat was founded in 2013, and ever since, she has grown tremendously beyond the founders' projection, cutting edge across other top tech firms globally. 

The founders Urška Sršen and Sando Mur  having enjoyed the growth and expansion pace needed further growth and development, they believed this could be achieved by analyzing the relationship the product users have with the various smart products in the industry.

## **The Business Objectives**

What are some trends in smart device usage?

How could these trends apply to Bellabeat customers?

How could these trends help influence Bellabeat's marketing strategy?

## The Business Task

Focus on one of Bellabeat's products and analyze the smart device data, to enable me gain insight into the consumer usage of the smart devices; the insight would guide me on the best marketing strategy for the company.

### The Deliverables

This involves the following:

- A clear summary of the business task. 

 - A description of all data sources used. 
   
- The documentation of any cleaning or manipulation of data. 

 - A summary of my analysis. 

- Supporting visualizations and key findings. 

- My top high-level content recommendations are based on your analysis.


**The Business Stakeholders** 

- Urška Sršen: Bellabeat’s co-founder and Chief Creative Officer. 

- Sando Mur: Mathematician and Bellabeat’s cofounder; a key member of the Bellabeat executive team. 

- Bellabeat marketing analytics team: A team of data analysts responsible for collecting, analyzing, and reporting data that helps guide Bellabeat’s marketing strategy. 

**The Business's Products**

Bellabeat app: The Bellabeat app provides users with health data related to their activity, sleep, stress, menstrual cycle, and mindfulness habits. 

Leaf: Bellabeat’s classic wellness tracker can be worn as a bracelet, necklace, or clip. The Leaf Tracker connects to the Bellabeat app to track activity, sleep, and stress. 

Time: This wellness watch combines the timeless look of a classic timepiece with smart technology to track user activity, sleep, and stress. The Time watch connects to the Bellabeat app to provide you with insights into your daily wellness. 

# STEP 2: PREPARE

Here, we explore the data being used; its credibility and limitations.

Information on Data Source:

The data is available publicly on Kaggle, the link is thus: Fitbit Fitness Tracker Data (kaggle.com) 

The data was drawn from 30 Fitbit users, through their fitness trackers. 

The data collected were: a. the heart rate, sleep rate, steps, and daily/physical activities which are recorded in minutes.


# THE ROCCC

The Reliable, Original, Comprehensive, Current, and Cited acronym is the benchmark and criteria of a very good data.  For the data used:

Reliable - LOW: 30 respondents are not enough to make inferences and predictions.

Original - LOW: There is a third-party provider (Amazon Mechanical Turk), which can alter the data.

Comprehensive - MED: Apart from the relatively low sample size, the physical activities, sleep monitoring, heart rate, etc were all measured in minutes, which is quite extensive. 

Current - LOW: The data was gathered in 2016 (8 years from 2024). This is outdated when it comes to fitness.

Cited - LOW: The data was gathered through  a third party, hence the source is not known.


**Data Selection**

The following data were selected:

dailyActivity_merged.csv

dailyCalories_merged.csv

dailyIntensities_merged.csv

dailySteps_merged.csv

sleeoDay_merged.csv

weightLogInfo_merged.csv


**Tools Used**

The following tools were used:

Excel Spreadsheet: This is used for cleaning the data and filtering some data.

R Studio: R Studio statistical software is used for making explorative analyses and visualizing the output.

Google Query / My SQL: this is also used for cleaning and analysis of some of the data.


# STEP 3: PROCESS


We will explore the data; this will be achieved by:

cleaning the data: I will check for null values and duplicate values, I will filter the values as well to ease with the cleaning.

I will format the dates from long to short dates, to trim down the hours and avoid complexities.

lastly, I will write queries to extract information and insight from the data.

## DATA OBSERVATION

Below is a screenshot of the general view of the first data set: dailyActivity_merged.

![a3](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/072ce2f9-157c-44c5-85e2-5e447bb5e9e4)
Dataset of Daily Activity

The above picture is a snipet of one of our datasets, the daily activity. We outlined the cleaning process below:

1. Using the filter and sort function of the pivot table, we checked for missing values in all 6 data sets, but we found none. All the values are consistent.

2. Also, to confirm the uniqueness of the customer's identity, we used the pivot table to count the number of unique identities, we discovered that it was 33, as against the 30 we were given. 

3. We formatted the date to "DDMMYYYY", using the text-to-columns formatting function.

4. Using the text-to-column and weekday functions, we converted the formatted dates into weekdays. This will give more insights into the analysis.

5. We summed the activities (very active, moderate, light and sedentary) and the number of times each was done.

6. We reduced all the decimal points in all the datasets to 2 decimal places.

![a4](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/e3c2cf05-d147-4b07-bc0f-56cad3c92805)
Dataset for Daily Intensity

The above table is a screenshot of the activities table, alongside the the distance covered in the activities.
Next: We further use Google Query to confirm the number of unique Identity from the data sets.

![a6](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/2c113192-2935-4f54-b584-9fc8a295f36b)

![a6](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/73a903f1-3c6d-474b-9ccb-52e128afd635)

The queries indicated that the daily activity and daily calorie datasets each have 33 unique identifiers. Similar queries for the remaining datasets yielded the following results:
Daily Intensity - 33 unique identifiers.
Daily Step - 33 unique identifiers.
Sleep Day - 24 unique identifiers.
Weight Log - 8 unique identifiers.

# STEP 4: ANALYSE USING SQL (GOOGLE QUERY) AND R

First, we check for the days of the week where they are most active.

`SELECT
WeekDays,
COUNT (WeekDays) AS Wd
FROM
`diogor-project.Project_data.DailyActiveMerge` D
GROUP BY WeekDays
ORDER by Weekdays DESC}`


Tuesday - 152

Friday - 152

Saturday - 149

Thursday -125

Sunday - 125

Wednesday - 122

Monday - 112

The vast majority of the users, 16.2% prefer to work out on Tuesday and Friday.  This is followed by 15.9% who choose to exercise on Saturday, and 13.3% who picked Thursday and Sunday; 

Next, we measure the very active distance, the week day it usually occur and the level of calories expended for the distances walked.

`SELECT
  VeryActiveDistance,
  VeryActiveMinutes,
  LightActiveDistance,
  WeekDays,
  Calories
FROM
  `diogor-project.Project_data.DailyActiveMerge` AS D
ORDER BY
  VeryActiveDistance DESC
LIMIT 5`


![a7](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/4791c5bb-78f6-4f1c-9509-04de1cb541be)

`SELECT
  WeightKg,
  BMI
FROM
  `diogor-project.Project_data.WeightLog`
WHERE
  BMI > 20 AND BMI < 25
ORDER BY
  WeightKg ASC;`

![a8](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/27eae06c-e259-41e1-8919-cb555fae3721)
Output showing Weight(Kg) and BMI between 20 and 25

`SELECT
  WeightKg,
  BMI
FROM
  `diogor-project.Project_data.WeightLog`
WHERE
  BMI > 25
ORDER BY
  WeightKg ASC;`

  ![a8](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/8f5b9fd2-65b9-4359-9ed1-4aaa24162199)
  Output showing Weight(Kg) and BMI above 25

  There is a connection between the BMI and the weight in Kg; Increased Kilogram in weight resulted in the increase in BMI. We will further proof it using the R correlation.

Next: We group the users according to their activity level to know those who are very active, moderately active and light active.

`SELECT Id,
       COUNT(Id) AS Total_Active,
       CASE
           WHEN COUNT(Id) BETWEEN 25 AND 31 THEN 'VERY ACTIVE'
           WHEN COUNT(Id) BETWEEN 15 AND 24 THEN 'MODERATE'
           WHEN COUNT(Id) BETWEEN 0 AND 14 THEN 'LIGHT'
       END AS Activity_Level
FROM `diogor-project.Project_data.DailyActiveMerge`
GROUP BY Id;`

29 (88%) Users are very active, 3 (9%) users are moderate, while 1 (3%) users are light. This indicates that the vast majority of the users are very active.

We further find te trends and pattern in the data using R.

We load the data into R studio:

`getwd()
setwd("C:/Users/User/OneDrive/Documents/cdata")
DailyActivity <- read.csv("dailyActivity_merged.csv")
DailyCalories <- read.csv("dailyCalories_merged.csv")
DailyIntensities <- read.csv("dailyIntensities_merged.csv")
DailySteps <- read.csv("dailySteps_merged.csv")
SleepDay <- read.csv("sleepDay_merged.csv")
WeightLog <- read.csv("weightLogInfo_merged.csv")`

Next, we check for the distinct number of users... to be double sure.

`
activity <- length(unique(DailyActivity$Id))
calorie <- length(unique(DailyCalories$Id))
intensity <- length(unique(DailyIntensities$Id))
steps <- length(unique(DailySteps$Id))
sleep <- length(unique(SleepDay$Id))
weight <- length(unique(WeightLog$Id))
`

activity  - 33

calorie - 33

Intensity - 33

steps - 33

sleep - 24

weight - 8

`packages_to_install <- c("ggplot2", "tidyverse", "dplyr", "tidyr", "janitor", "readr", "lubridate")`

# Check for missing packages and install them
`install_packages <- packages_to_install[!packages_to_install %in% installed.packages()[, "Package"]]
if (length(install_packages) > 0) {
  install.packages(install_packages, dependencies = TRUE)
}`

We load the data next:

# Load the installed packages

`library(ggplot2)
library(tidyverse)
library(dplyr)
library(tidyr)
library(janitor)
library(readr)  # Corrected from 'reader' to 'readr'
library(lubridate)_`

Next, we group the total step dataset according to light activity, average activity and full activity, after which we summarize them in percentages.

`DailySteps <- DailySteps %>%
  mutate(ActivityLevel = case_when(
    StepTotal < 2000 ~ "Inactive",
    StepTotal >= 2000 & StepTotal < 6000 ~ "Light Activity",
    StepTotal >= 6000 & StepTotal < 13000 ~ "Moderate Activity",
    StepTotal >= 13000 ~ "High Activity",
    TRUE ~ "Unknown" # Default level for any other cases
  ))`

# Group by ActivityLevel and summarize StepTotal in percentage
`summary_percentage <- DailySteps %>%
  group_by(ActivityLevel) %>%
  summarize(Percentage = sum(StepTotal) / sum(DailySteps$StepTotal) * 100)`

# View the summarized percentage
```print(summary_percentage)```


# Merge datasets using 'ID' as the unique key

```merged_dataset <- inner_join(DailySteps, SleepDay, by = "Id")```

# Create a new column for sleep per activity level

`merged_dataset <- merged_dataset %>%
  mutate(SleepAmount = case_when(
    ActivityLevel == "Inactive" ~ TotalMinutesAsleep,
    ActivityLevel == "Light Activity" ~ TotalMinutesAsleep,
    ActivityLevel == "Moderate Activity" ~ TotalMinutesAsleep,
    ActivityLevel == "Very Active" ~ TotalMinutesAsleep,
    TRUE ~ 0  # Default value for other cases
  ))`

# Summarize sleep amount by activity level

`summary_sleep <- merged_dataset %>%
  group_by(ActivityLevel) %>%
  summarize(AverageSleep = mean(SleepAmount, na.rm = TRUE))`

# Display the sleep summary

`print(summary_sleep)`

![a12](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/873b35a8-70f3-48ad-a297-140b81f98adf)
Activity level with the average time.

From the data above, it is clear that the users who did light and moderate activities had less sleep 6hr.52mins, 6hrs.95mins than those who did light activity or were inactive completely. at 7hr.15mins and 7hr.28mins respectively.

# 5. SHARE
At  the share level, we visualise different relationships and discover the correlations between trends and patterns in Bella beat.

We start by measuring the relationship between body weight in KG, and Body Mass Index (BMI). BMI is medically used to ascertain the health condition of a human being. High BMI say, from 25 to 30, 30 to 35, 35 to 40, 40 and above all have health implications. The code and visuals below will explain what causes the BMI to increase.

`R
ggplot(WeightLog, aes(x = WeightKg, y = BMI)) +
  geom_point(aes(color = WeightKg), size = 3) +
  geom_point(aes(color = BMI), size = 3) +
  geom_smooth(method = "lm", se = FALSE, linetype = "solid", color = "black") + # Linear regression line
  scale_color_manual(values = c("WeightKg" = "blue", "BMI" = "red")) +
  labs(title = "Scatterplot of WeightKg vs. BMI",
       x = "Weight (Kg)",
       y = "BMI")
`

![a13](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/360684bd-a526-41e1-8911-05ca9bda3f67)
Scatterplot for BMI vs Weight(Kg)

# Merge datasets using 'Id' as the unique key
```merged_data <- inner_join(DailyCalories, DailyIntensities, by = "Id")```

# Trim Total_dist to two decimal places
```merged_data <- merged_data %>%```
  ```mutate(Total_dist.km. = round(Total_dist.km., 2))```

# Create a scatterplot with a gradient from light blue to dark blue for Calories and Total_dist, and add a line
```ggplot(merged_data, aes(x = Calories, y = Total_dist.km.)) +`
  geom_point(aes(color = Calories), size = 3) +
  geom_smooth(method = "lm", se = FALSE, linetype = "solid", color = "blue") +  # Line in blue
  scale_color_gradient(low = "#66CCFF", high = "#00274C") +  # Gradient from light blue to dark blue
  labs(title = "Calories vs. Total Distance Scatterplot",
       x = "Calories Burned",
       y = "Total Distance (km)")```

![a14](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/00985fef-1311-442f-b94d-93106763a4c9)
Scatterplot of calories vs total distance

The relationship between the distance covered and the calories burned is a positive one. It shows that as people engage more in the exercise by walking or running longer kilometres, they burn more calories and hence reduce their body mass index to a very normal body mass.

Next, we visualize the days of the week alongside the very active days, this will enable us to know the days of the week that have the highest number of very active participants. We will do the same for the inactive.

# Rank the weekdays by VeryActiveDistance
```DailyActivity <- transform(DailyActivity, WeekDays = reorder(WeekDays, rank(-VeryActiveDistance)))```

# Create a horizontal histogram with green fill
```ggplot(DailyActivity, aes(x = VeryActiveDistance, y = WeekDays)) +`
  geom_bar(stat = "identity", fill = "green") +
  labs(title = "Very Active Distance by Weekdays",
       x = "Very Active Distance",
       y = "Weekdays")```

![a15](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/58810182-b31b-43bc-8bc1-77511a373d50)
Histogram depicting the distance covered on weekdays during high activity periods

We repeat the same for the Inactive Distance and know the exact day people chose to be inactive:::

# Rank weekdays by Sedentary Active Distance

``DailyActivity <- transform(DailyActivity, WeekDays = reorder(WeekDays, rank(-SedentaryActiveDistance)))``

# Create a horizontal histogram with green fill

```ggplot(DailyActivity, aes(x = SedentaryActiveDistance, y = WeekDays)) +``
  geom_bar(stat = "identity", fill = "green") +
  labs(title = "Sedentary Active Distance by Weekdays",
       x = "Sedentary Active Distance",
       y = "Weekdays")```

![a16](https://github.com/diogor1/Bellabeat_fitness/assets/30722736/ad2f874a-d953-4cb8-8cf6-5bf528216697)
Sedentary Versus Active Days: A Weekday Comparison

# 6. ACT
This is the last phase that comes with recommendations: First of all, I will state the insights I have discovered from the analysis:

## Our Discovery:

* There are more people who actively use the device than inactive people. 58% are moderately active, while 28% are extremely active. At the same time, 13% and 0.8% are light active and inactive respectively.

* We further checked their sleep pattern and discovered that two more active groups usually have slightly less sleep time. They invest more time in their work life.  6hr.52mins and 6hr.95 mins as against 7hr.15 and 7hr.28mins.

* A strong positive correlation exists between the user's weight and body mass index. The higher the weight, the higher the BMI.

* We checked the days of the week when the users are more proactive, we discovered Saturday to be the highest; this is followed by Tuesday. These are the days with more people being more proactive and vibrant. They went as far as 21.9 km and 21.7km, respectively, and burned over 4500 calories.

* We also checked for the days of the week with sedentary or inactive participation,  we discovered it to be Thursday, followed by Monday.

* There is a positive correlation between calories burned and total distance covered in the exercise.

## Our Recommendation : 

* More weekends could also be utilized, such as Fridays and Sundays, instead of only Saturdays. This would get people to balance out their work and exercise timing.

* There is a positive correlation between high activity and low sleep rate, those with extreme activity should put in some time to sleep more to achieve a balanced healthy life. Such people should also be appreciated for the extra mile they go to make their lives better.

* Those who are inactive could get a sort of reminder to help them boost their pace. A health memo could be published in the app to serve as a reminder of why they need to step up.

* Users should also be sensitized about the meaning of body mass index (BMI), how to measure it, how to use it to know the state of one's health, and the connection it has with body weight. This will improve their awareness and usage of the kits for the greater good.

* The users should also be sensitized on the relationship between the distance covered, the number of steps taken per time, and the level of calories one could burn in the process.

* If possible, very active users should get a slight discount or a sort of benefit coin for being proactive. This will motivate others.
