# PowerBI Data Analysis

## Hospital Emergency Room Analysis

### Table of Contents

- [Project Description](#project-description)
- [Data Source](#data-source)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Tools](#tools)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results/Findings](#resultsfindings)
  

### Project Description
The project aims to create a comprehensive dashboard to analyze the hospital emergency room. We have three dashboards to analyze the data. One is a month-based analysis, where we can see how many patients visited the hospital and whether they were admitted. Another is a consolidated one, where we have analyzed the entire patient record. The last one is a table showing the patient records so that anyone can filter out the patient records.

![Hospital Emergency Room Dashboard image](Hospital%20Emergency%20Dashboard.png)

### Data Source
- Hospital Emergency Room Data: The data is available in the "Hospital ER_Data.csv" file which contains all the information about the hospital emergency room.

### Tools
- Power BI Desktop: For data cleaning and visualization.

### Data Cleaning and Preparation
- In the Power BI Desktop, we have inserted the csv data. I have checked each column for missing values and formatting issues. I have also checked whether the datatypes assigned to each column are correct. I have also created a new table as a time table which has the data of patient visited date, month, year, time, and all.

### Exploratory Data Analysis
Performed some exploratory data analysis to find some information about key questions like
- The total number of patients visited the hospital.
- Which day of the week is the busiest day and what time of the day is the busiest hour?
- How many patients came as a referral?
- How many patients got admitted to the hospital?
- What is the average time patient has to wait before seeing the doctor and whether it is within the time limit or exceeding it?

### Data Analysis
To find the answer to the key questions, I have written some query in the MySQL as
``` PowerBI
Age Group = 
SWITCH(
    TRUE(), 'Hospital ER_Data'[Patient Age] >= 100, "100+",
    'Hospital ER_Data'[Patient Age] >= 90, "90-99",
    'Hospital ER_Data'[Patient Age] >= 80, "80-89",
    'Hospital ER_Data'[Patient Age] >= 70, "70-79",
    'Hospital ER_Data'[Patient Age] >= 60, "60-69",
    'Hospital ER_Data'[Patient Age] >= 50, "50-59",
    'Hospital ER_Data'[Patient Age] >= 40, "40-49",
    'Hospital ER_Data'[Patient Age] >= 30, "30-39",
    'Hospital ER_Data'[Patient Age] >= 20, "20-29",
    'Hospital ER_Data'[Patient Age] >= 10, "10-20",
    "0-9"
    )
```
``` PowerBI
Time_Table = CALENDAR(MIN('Hospital ER_Data'[Patient Admission Date]),MAX('Hospital ER_Data'[Patient Admission Date]))
```

### Results/Findings
- Saturday is the busiest day of the week.
- Midnight time is the busiest time when patients are visiting.
- Around 60% of the patients have to wait longer than the usual waiting time of 30 minutes.
- Around 5.5k patients are non-referral patients.
- Young people and adults are the ones who are visiting the hospital.
