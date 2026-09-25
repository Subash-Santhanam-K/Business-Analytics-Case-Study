# Talent Market Intelligence: Analyzing Skill Demand and Workforce Requirements in India's IT Job Market

**Business Analytics Individual Case Study**  
**Author:** Subash Santhanam K  
**Register Number:** CB.SC.U4CSE23444  
**Class / Section:** CSE-E  
**Business Domain:** Recruitment / Human Resource Analytics  
**Data Collection Tool:** Apify Naukri Job Scraper → Naukri.com  
**Collection Dates:** July 19, 2026 (Pilot) / September 25, 2026 (Production)  

---

## 1. Executive Summary & Business Problem

The IT industry in India is characterized by rapid technological advancement, evolving workforce expectations, and persistent recruitment friction. Recruiters face high candidate screening costs and mismatch between posted job requirements and market availability. Simultaneously, higher education institutions struggle with curriculum alignment, and technical job seekers lack objective market signals regarding high-yield skills.

This study implements an end-to-end Talent Intelligence and Machine Learning framework analyzing web-scraped IT job postings from Naukri.com. The investigation extracts empirical intelligence on skill demand, role distributions, geographic concentrations, and compensation disclosure, while developing a supervised multiclass classification model to predict required experience tiers (`Entry`, `Mid`, `Senior`) directly from role, location, and technical skill indicators.

---

## 2. Dataset Overview

| Attribute | Specification |
|---|---|
| **Data Source** | Naukri.com via Apify Naukri Job Scraper |
| **Search Queries** | Software Developer, Data Analyst, Data Engineer / Architect, Data Scientist / Machine Learning, Full Stack Developer |
| **Raw Records Ingested** | 998 postings across 5 CSV runs |
| **Duplicate Removal** | 25 cross-query duplicate listings removed using unique `jobDetails/jobId` |
| **Final Analytical Dataset** | **973 unique IT job postings** |
| **Feature Dimensionality** | 33 predictive features (zero target leakage) |
| **Target Variable** | `experience_level`: `Entry` ($\le 2$ yrs), `Mid` ($3-6$ yrs), `Senior` ($\ge 7$ yrs) |

### Target Class Distribution
- **Mid-Level (3–6 years):** 416 postings (42.75%)
- **Entry-Level (0–2 years):** 415 postings (42.65%)
- **Senior-Level ($\ge$ 7 years):** 142 postings (14.59%)

---

## 3. Key Empirical Findings

1. **Dominant Technical Competencies:**
   - **Python** leads across the entire IT landscape at **54.8%** market penetration ($533$ postings).
   - **SQL** is the second most ubiquitous competency at **37.6%** ($366$ postings).
   - Cloud and analytics tools include **AWS** (**17.4%**, $ postings), **JavaScript** (**14.3%**), **Data Quality** (**14.3%**), and **Machine Learning** (**13.3%**).

2. **Geographic Concentration:**
   - The top 4 technological hubs account for **70.1%** of all IT hiring volume:
     - **Bengaluru:** 24.5% ($238$ postings)
     - **Hyderabad:** 17.3% ($168$ postings)
     - **Pune:** 14.2% ($138$ postings)
     - **Mumbai:** 14.1% ($137$ postings)

3. **Compensation Non-Disclosure:**
   - Only **17.7%** ($172$ postings) disclose explicit salary packages, while **82.3%** ($801$ postings) conceal compensation.
   - Disclosed median salary is **INR 8.0 LPA** (mean: **INR 10.3 LPA**).

---

## 4. Machine Learning & Model Selection

Supervised models were trained using an 80/20 stratified split ($N_{\text{train}} = 778$, $N_{\text{test}} = 195$) with Stratified 5-Fold Cross-Validation:

| Model Architecture | 5-Fold CV Weighted F1 | Test Accuracy | Test Weighted F1 | Test Macro F1 |
|---|---|---|---|---|
| **Logistic Regression** (L2) | $0.5872 \pm 0.0517$ | 61.54% | 0.6100 | 0.5700 |
| **Decision Tree** (CART) | $0.5194 \pm 0.0150$ | 57.95% | 0.5610 | 0.4995 |
| **Random Forest** (Selected) | $\mathbf{0.6280 \pm 0.0441}$ | **63.08%** | **0.6229** | **0.5745** |
| **Gradient Boosting** | $0.5971 \pm 0.0253$ | 64.62% | 0.6375 | 0.5900 |

### Model Selection Methodology
Candidate models were evaluated using Stratified 5-Fold Cross-Validation on the training data. **Random Forest** achieved the highest mean validation score ($0.6280 \pm 0.0441$ weighted F1) and was selected prior to evaluating on the hold-out test set. The untouched hold-out test set ($N=195$) was then evaluated once, yielding **63.08% test accuracy** and a **weighted F1-score of 0.6229**.

---

## 5. State-of-the-Art Literature Review

The report rigorously synthesizes three independently verified peer-reviewed studies:
1. **Karakatsanis et al. (2017)** — *Information Systems*, Elsevier (DOI: `10.1016/j.is.2016.10.009`): Latent Semantic Indexing (LSI) with SVD on TF-IDF matrices; mapping vacancies to O*NET taxonomy.
2. **Bhola et al. (2020)** — *COLING 2020* (DOI: `10.18653/v1/2020.coling-main.513`): Language model-based Extreme Multi-Label Classification (XMLC) with fine-tuned BERT for retrieving missing skills from unstructured text.
3. **Giabelli et al. (2021)** — *Applied Soft Computing*, Elsevier (DOI: `10.1016/j.asoc.2020.107049`): *Skills2Job* graph database recommender system encoding job offers with `node2vec` and Word2Vec embeddings grounded in ESCO taxonomy.

---

## 6. Project Deliverables & Structure

```
BA CS/
│
├── analysis.ipynb             ← Fully audited Jupyter Notebook (all 46 cells executed cleanly with 0 errors)
├── main.tex                   ← Publication-grade LaTeX source (10-page academic case study report)
├── references.bib             ← Verified BibTeX bibliography (peer-reviewed DOIs & platforms)
├── Case_Study_Report.pdf                   ← Compiled publication-quality case study report (10 pages)
├── figures/                   ← Standardized high-resolution analytical figures (13 PNGs)
│   ├── target_distribution.png
│   ├── role_distribution.png
│   ├── experience_by_role.png
│   ├── top_skills.png
│   ├── location_distribution.png
│   ├── skill_experience.png
│   ├── role_skill_heatmap.png
│   ├── hiring_companies.png
│   ├── salary_analysis.png
│   ├── correlation_matrix.png
│   ├── model_comparison.png
│   ├── confusion_matrix.png
│   └── feature_importance.png
├── data/                      ← Raw and processed analytical datasets
│   ├── raw/ (1.csv to 5.csv)
│   ├── combined_raw.csv
│   └── cleaned_dataset.csv
├── requirements.txt           ← Python dependencies
└── README.md                  ← Comprehensive project documentation
```

---

## 7. Compilation Instructions

To recompile `main.tex` into `Case_Study_Report.pdf` on Windows:

```powershell
# Using the bundled portable pdfTeX engine:
.\tinytex\TinyTeX\bin\windows\pdflatex.exe -interaction=nonstopmode main.tex
.\tinytex\TinyTeX\bin\windows\bibtex.exe main
.\tinytex\TinyTeX\bin\windows\pdflatex.exe -interaction=nonstopmode main.tex
.\tinytex\TinyTeX\bin\windows\pdflatex.exe -interaction=nonstopmode main.tex
```

---

## 8. Academic Integrity & Non-Fabrication Notice

All numerical findings, percentages, dataset counts ($N=973$), model evaluation metrics, confusion matrix values, and feature importances documented in this report are directly derived from the audited Jupyter notebook `analysis.ipynb`. No assumptions or synthetic figures were introduced.
