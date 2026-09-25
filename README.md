# Talent Market Intelligence: Analyzing Skill Demand and Workforce Requirements in India's IT Job Market

Business Analytics Individual Case Study

Author: Subash Santhanam K  
Register Number: CB.SC.U4CSE23444  
Class / Section: CSE-E  
Business Domain: Recruitment / Human Resource Analytics  

Data Collection Tool: Apify Naukri Job Scraper  
Source: Naukri.com  
Collection Dates: July 19, 2026 (Pilot) and September 25, 2026 (Main Collection)

---

## 1. About the Project

I chose the Indian IT job market for this case study because the skills mentioned in job postings change frequently and different roles often require different combinations of technical skills.

In this project, I collected IT job postings from Naukri.com using the Apify Naukri Job Scraper. I used the collected data to study the demand for technical skills, job roles, locations, experience levels and salary information.

I also built a classification model to predict the experience level mentioned in a job posting using information such as the job role, location and technical skills.

The main focus of my analysis is to understand what the collected job postings indicate about the current IT hiring requirements in the sample.

---

## 2. Objectives

I used the collected job postings to answer the following questions:

- Which technical skills appear most frequently in the collected IT job postings?
- Which job roles have the highest representation in the dataset?
- How are job postings distributed across different experience levels?
- Which Indian cities have the highest number of postings in my sample?
- How do technical skill requirements vary across experience levels?
- Which skills are commonly associated with different job roles?
- How much salary information is disclosed in the collected postings?
- Can the experience level of a posting be predicted from its role, location and listed skills?
- How does my approach compare with methods used in published studies on job-market and skill analysis?

---

## 3. Data Collection

I collected the data using the Apify Naukri Job Scraper.

I used five search queries:

1. Software Developer
2. Data Analyst
3. Data Engineer / Architect
4. Data Scientist / Machine Learning
5. Full Stack Developer

The five CSV files are stored in the `data/raw/` directory.

The initial collection contained 998 job postings. Since the same job can appear under more than one search query, I checked the `jobId` values and removed duplicate postings.

After removing 25 duplicate postings, I obtained 973 unique job postings for the analysis.

The data used in the project was collected from job advertisements and therefore represents the requirements stated in those advertisements rather than actual hiring outcomes.

---

## 4. Dataset

The project contains both the original collected files and the processed dataset.

The main files are:

```text
data/
├── raw/
│   ├── 1.csv
│   ├── 2.csv
│   ├── 3.csv
│   ├── 4.csv
│   └── 5.csv
│
├── combined_raw.csv
└── cleaned_dataset.csv
