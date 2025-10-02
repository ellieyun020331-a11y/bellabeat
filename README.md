# bellabeat
Bellabeat case study
## Background Information
This project is based on Google Data Analytics Case Study : Bellabeat.
Bellabeat is a high-tech company rhat manufactures health-focused products for women with great potential to become a larger player in the flobalsma device market. The company is interested in using data to understand consumer behaviour and discover insights that could help guide marketing strategies for its products. 

## Data
For this case study, I analyzed public Fitbit Fitness Tracher data from Kaggle. (https://www.kaggle.com/datasets/arashnic/fitbit)
The dataset contains personal fitness tracker data from 30 Fitbit users who consented to share their daily activity, steps, heart rate, calories, and sleep information over a two-month period (March–May 2016).
It includes daily logs of:
	•	Activity: steps, distances, intensities, calories burned
	•	Sleep: minute-level sleep states
	•	Heart rate: second-level BPM readings
	•	Weight logs: optional user-entered weight, BMI, body fat percentage

The data contains limitation of sample size and lack of informations.

For this analysis, I worked with two monthly exports of Fitbit data:
	•	mturkfitbit_export_3.12.16–4.11.16 (March 12 – April 11, 2016)
	•	mturkfitbit_export_4.12.16–5.12.16 (April 12 – May 12, 2016)

Each folder contained multiple CSV files with daily, hourly, and minute-level logs, such as:
	•	Daily activity (steps, distance, sedentary minutes, calories)
	•	Heart rate (seconds-level)
	•	Hourly steps, calories, intensities
	•	Minute-level calories, steps, intensities, and sleep states
	•	Weight logs

## Business task
:  Analyze public smart-device usage data (Fitbit) to understand consumer activity, sleep, and wellness patterns, then translate these insights into actionable marketing recommendations for one Bellabeat product.

## Data Preparation & Transformation
All CSV files from the two Fitbit export folders were uploaded into R.
	•	Data from the two months was merged into unified tables (daily, hourly, minute, heart rate, weight).
	•	Columns were standardized (lowercase names).
	•	Duplicate records were removed.
	•	Dates and timestamps were parsed into proper Date / POSIXct formats.
- Aggregated sleep data
	•	Transformed minuteSleep_merged.csv into a daily sleep summary (sleep_day):
	•	totalminutesasleep
	•	totaltimeinbed
	•	sleep_hours (hours slept)
	•	sleep_efficiency (ratio of minutes asleep to time in bed)
- Filtered unrealistic values
	•	Removed extreme outliers such as:
	•	totalsteps > 60,000 per day
	•	sleep_efficiency outside 0.5–1.0
	•	Implausible weight values (<30kg or >200kg)
- Arranged datasets
	•	Sorted by id, date, and (where relevant) hour or minute for easier joining and visualization.
- Created combined tables
	•	Built act_sleep by joining daily activity + daily sleep (on id + date) for correlation analysis.

## analysis 
**Steps vs Sleep Hours**
![Steps vs Sleep](figs/leaf_steps_vs_sleep.png)


