# Talent Market Intelligence: Analyzing Skill Demand and Workforce Requirements in India's IT Job Market

**Business Analytics Individual Case Study**

**Author:** Subash Santhanam K  
**Register Number:** CB.SC.U4CSE23444  
**Class / Section:** CSE-E  
**Business Domain:** Recruitment / Human Resource Analytics  

**Data Collection Tool:** Apify Naukri Job Scraper  
**Source:** Naukri.com  
**Collection Dates:** July 19, 2026 (Pilot) and September 25, 2026 (Main Collection)

---

## 1. About the Project

I chose the Indian IT job market for this case study because the skills mentioned in job postings change frequently and different roles often require different combinations of technical skills.

In this project, I collected IT job postings from Naukri.com using the Apify Naukri Job Scraper. I used the collected data to study the demand for technical skills, job roles, locations, experience levels and salary information.

I also built a classification model to predict the experience level associated with a job posting using information such as the job role, location and technical skills.

The main focus of my analysis is to understand the patterns present in the collected IT job postings and use them to derive useful insights about hiring requirements.

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
- How does my approach compare with methods used in published studies related to job-market and skill analysis?

---

## 3. Data Collection

I collected the data using the Apify Naukri Job Scraper.

I used five search queries:

1. Software Developer
2. Data Analyst
3. Data Engineer / Architect
4. Data Scientist / Machine Learning
5. Full Stack Developer

The five CSV files generated from these searches are stored in the `data/raw/` directory.

The initial collection contained 998 job postings. Since the same job can appear under more than one search query, I checked the `jobId` values and removed duplicate postings.

After removing 25 duplicate postings, I obtained 973 unique job postings for the analysis.

The data represents information available in job advertisements. Therefore, the analysis describes the requirements mentioned in the collected postings rather than actual hiring outcomes.

---

## 4. Dataset

The project contains the original collected files as well as the processed datasets.

The main data files are organised as follows:

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
```

`combined_raw.csv` contains the data obtained after combining the five CSV files.

`cleaned_dataset.csv` contains the variables used for the main analysis and machine learning model.

The final analytical dataset contains 973 unique job postings.

---

## 5. Data Preparation

I performed the following steps before starting the analysis:

- Loaded the five CSV files.
- Checked the columns and data types.
- Combined the five files into a single dataset.
- Checked for duplicate job postings using `jobId`.
- Removed duplicate postings.
- Checked missing values.
- Extracted and standardised technical skills.
- Merged similar skill names where required.
- Standardised location names.
- Created broader job-role categories.
- Extracted minimum and maximum experience values.
- Created an experience-level variable.
- Created the variables required for the machine learning model.
- Checked the final dataset before starting the analysis.

For the classification task, I grouped the postings into three experience levels:

- **Entry:** 0–2 years
- **Mid:** 3–6 years
- **Senior:** 7 years and above

---

## 6. Exploratory Analysis

I used the cleaned dataset to analyse different aspects of the collected job postings.

The notebook contains visualisations for:

- Experience-level distribution
- Job-role distribution
- Experience level by job role
- Most frequently requested technical skills
- Location distribution
- Skill requirements across experience levels
- Job role and skill relationships
- Companies with the highest number of postings
- Salary disclosure
- Correlation between numerical variables

The analysis focuses on the patterns present in the collected sample. I do not treat the sample as a complete representation of the Indian IT job market.

---

## 7. Machine Learning

I treated experience level as a multiclass classification problem.

The target variable contains three classes:

- Entry
- Mid
- Senior

I used information from the job posting such as:

- Broad job role
- Location
- Number of listed skills
- Individual technical skill indicators

I kept the experience-related variables out of the predictor set so that the model would not directly receive the information used to create the target.

I divided the data into training and test sets using an 80/20 stratified split.

This resulted in:

- **Training records:** 778
- **Test records:** 195

I compared four machine learning models:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. Gradient Boosting

I used Stratified 5-Fold Cross-Validation on the training data to compare the models.

The cross-validation weighted F1 scores were:

| Model | 5-Fold CV Weighted F1 |
|---|---|
| **Random Forest** | **0.6280 ± 0.0441** |
| Gradient Boosting | 0.5971 ± 0.0253 |
| Logistic Regression | 0.5872 ± 0.0517 |
| Decision Tree | 0.5194 ± 0.0150 |

Random Forest had the highest mean cross-validation weighted F1 score, so I used it as the final model before evaluating the hold-out test set.

The final Random Forest results on the test set were:

| Metric | Result |
|---|---|
| **Accuracy** | **63.08%** |
| **Weighted F1** | **0.6229** |
| **Macro F1** | **0.5745** |

I also analysed the confusion matrix and feature importance of the final model.

---

## 8. Published Studies

I compared my approach with three published studies related to job-market, skills and recruitment analytics.

### Karakatsanis et al. (2017)

This study used text-mining techniques to analyse job vacancies and map vacancy information to occupational classifications.

The study used Latent Semantic Indexing and Singular Value Decomposition with TF-IDF representations.

### Bhola et al. (2020)

This work studied skill extraction from job-related text using language-model-based methods.

The approach used BERT-based modelling for extreme multi-label classification of skills.

### Giabelli et al. (2021)

This study introduced the Skills2Job approach for connecting job offers and skills using graph-based representations.

The work used techniques including node2vec and Word2Vec and incorporated the ESCO skills and occupations framework.

In my project, I used a tabular classification approach based on job role, location, skill count and individual skill indicators. This is different from the text-mining, language-model and graph-based approaches used in these studies.

The detailed comparison is included in the notebook and report.

---

## 9. Business Insights

Based on the job postings I collected, I identified several patterns that are useful for understanding the sample.

### For Recruiters

The frequency of technical skills provides an indication of the skills that appear repeatedly in the collected job advertisements.

The role and location distributions also show where different types of IT vacancies are concentrated in the sample.

### For Educational Institutions

The repeated appearance of programming, database, cloud and machine-learning-related skills provides useful information when reviewing technical training and curriculum content.

### For Training Providers

The combinations of skills appearing in different job roles can be used to design training paths covering related skills together.

### For Job Seekers

The analysis provides an indication of the technical skills that occur frequently in the collected IT vacancies.

The requirements also vary across experience levels, which can help in understanding how the skill profile changes between entry-level, mid-level and senior postings.

---

## 10. Limitations

There are some limitations to my analysis.

First, the dataset comes from Naukri.com, so the results represent the postings available through this source and do not cover every IT vacancy in India.

Second, I used a fixed set of five search queries. Other search terms could produce additional types of job postings.

Third, job advertisements can contain different descriptions for similar roles and skills, even when the underlying requirement is similar.

Fourth, salary information is not available for every posting, so the salary analysis only uses postings where compensation information was disclosed.

Finally, the machine learning model predicts the experience category associated with a job posting. It does not predict an individual's actual experience or whether a candidate will be hired.

---

## 11. Project Files

The repository is organised as follows:

```text
Business-Analytics-Case-Study/
│
├── CSE23444_Notebook.ipynb
├── CSE23444_Report.pdf
├── README.md
│
└── data/
    ├── raw/
    │   ├── 1.csv
    │   ├── 2.csv
    │   ├── 3.csv
    │   ├── 4.csv
    │   └── 5.csv
    │
    ├── combined_raw.csv
    └── cleaned_dataset.csv
```

- `CSE23444_Notebook.ipynb` contains my analysis, visualisations, machine learning implementation and results.
- `CSE23444_Report.pdf` contains my final case study report.
- The `data/raw/` folder contains the five collected CSV files.
- `combined_raw.csv` contains the combined data.
- `cleaned_dataset.csv` contains the cleaned data used for the analysis and modelling.

---

## 12. References

1. Karakatsanis, I., et al. (2017). Text mining for job vacancy analysis and occupational classification. *Information Systems*.  
   DOI: [10.1016/j.is.2016.10.009](https://doi.org/10.1016/j.is.2016.10.009)
2. Bhola, S., et al. (2020). Skill extraction from job descriptions using language-model-based methods. *Proceedings of COLING 2020*.  
   DOI: [10.18653/v1/2020.coling-main.513](https://doi.org/10.18653/v1/2020.coling-main.513)
3. Giabelli, A., et al. (2021). Skills2Job: A graph-based approach for connecting skills and job offers. *Applied Soft Computing*.  
   DOI: [10.1016/j.asoc.2020.107049](https://doi.org/10.1016/j.asoc.2020.107049)
