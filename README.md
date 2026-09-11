#  HR Employee Attrition Analysis — Power BI Dashboard

> Analyzing IBM HR employee data to uncover why employees are leaving — examining attrition patterns across departments, job roles, salary bands, age groups, marital status, business travel, and overtime to help HR teams reduce turnover and retain top talent.

---

Brief Summary
=============

An end-to-end HR analytics project on 1,470 IBM employees (35 features) — involving data modeling in Microsoft Fabric, DAX measure creation, and a 3-page interactive Power BI dashboard — to answer: **"What is the overall attrition rate, which departments are losing the most people, and is there a relationship between pay, age, and the decision to leave?"**

---

Overview
========

This project analyses IBM's HR employee dataset to surface actionable insights around employee attrition. With an overall attrition rate of 16.12% (237 out of 1,470 employees), the dashboard breaks down who is leaving — by department, job role, salary band, age group, marital status, overtime status, business travel frequency, and education field — helping HR leadership prioritize retention efforts where they matter most.

---

Problem Statement
=================

Employee attrition is a costly challenge for organizations — replacing an employee can cost 50–200% of their annual salary. IBM's HR team needs a clear, data-driven understanding of who is leaving and why.

**Questions To Be Answered:**

| # | Business Question |
|---|------------------|
| 1 | What is the overall attrition rate? |
| 2 | Which departments are losing the most people? |
| 3 | Is there a relationship between pay, age, and the decision to leave? |

**Core Business Question:**
> *"Why are employees leaving — and which departments, roles, salary bands, and demographics are at the highest attrition risk?"*

---

Dataset
-------

| Detail | Info |
|--------|------|
| File | `HR-Employee-Attrition.csv` |
| Records | 1,470 employees |
| Features | 35 columns |
| Target | `Attrition` — Yes (237) / No (1,233) |
| Source | IBM HR Analytics Dataset |

**Key Columns:**

| Column | Description |
|--------|-------------|
| `Age` | Employee age |
| `Attrition` | Target — Yes = Left, No = Stayed |
| `BusinessTravel` | Travel frequency — Travel_Frequently, Travel_Rarely, Non-Travel |
| `DailyRate` | Daily pay rate |
| `Department` | Sales / Research & Development / Human Resources |
| `DistanceFromHome` | Distance from home to workplace (km) |
| `Education` | Education level (1–5 scale) |
| `EducationField` | Field of education (Life Sciences, Medical, Marketing, etc.) |
| `EnvironmentSatisfaction` | Satisfaction with work environment (1–4) |
| `Gender` | Male / Female |
| `JobInvolvement` | Level of job involvement (1–4) |
| `JobLevel` | Seniority level (1–5) |
| `JobRole` | Role title (Sales Rep, Lab Technician, Manager, etc.) |
| `JobSatisfaction` | Job satisfaction rating (1–4) |
| `MaritalStatus` | Single / Married / Divorced |
| `MonthlyIncome` | Monthly salary |
| `NumCompaniesWorked` | Number of previous employers |
| `OverTime` | Whether employee works overtime — Yes / No |
| `PercentSalaryHike` | Last salary hike percentage |
| `PerformanceRating` | Performance rating (1–4) |
| `RelationshipSatisfaction` | Relationship with manager satisfaction (1–4) |
| `StockOptionLevel` | Stock option level (0–3) |
| `TotalWorkingYears` | Total years of work experience |
| `TrainingTimesLastYear` | Number of training sessions last year |
| `WorkLifeBalance` | Work-life balance rating (1–4) |
| `YearsAtCompany` | Years spent at the company |
| `YearsInCurrentRole` | Years in current job role |
| `YearsSinceLastPromotion` | Years since last promotion |
| `YearsWithCurrManager` | Years working with current manager |

**Engineered Columns (DAX / Power Query):**

| Column | Description |
|--------|-------------|
| `Age_Group` | Bucketed age groups — 18–25, 26–35, 36–45, 46–60 |
| `Salary_band` | Income buckets — Under 3K, 3K to 6K, 6K to 10K, Above 10K |
| `Attrition Rate` | DAX measure — Employees Left ÷ Total Headcount × 100 |

---

Tools & Technologies
--------------------

| Tool | Purpose |
|------|---------|
| **Microsoft Fabric** | Data lakehouse — `DF_HR` dataflow + `lh_HR` lakehouse + `HR_semantic_model` |
| **Power BI** | Interactive dashboard & reporting (`HR_analysis`) |
| **DAX** | Calculated measures — Attrition Rate, Employees Left, Avg Tenure of Leavers |
| **Power Query** | Data cleaning & transformation — Age Group, Salary Band bucketing |

---

Methods
-------

| Step | Description |
|------|-------------|
| **1. Data Ingestion** | Loaded `HR-Employee-Attrition.csv` into Microsoft Fabric via `DF_HR` dataflow into `lh_HR` lakehouse |
| **2. Semantic Model** | Built `HR_semantic_model` with proper data types, relationships, and column formatting |
| **3. Feature Engineering** | Created `Age_Group` (4 buckets) and `Salary_band` (4 buckets) in Power Query for segment analysis |
| **4. DAX Measures** | Built core KPI measures — `Attrition Rate %`, `Employees Left`, `Total Headcount`, `Average Income`, `Avg Tenure of Leavers` |
| **5. Dashboard — Overview** | KPI cards + Attrition by Department bar chart + Attrition Decomposition Tree (Department → Job Role → Salary Band) |
| **6. Dashboard — Deep Dive 1** | Attrition by Job Role table (color-coded) + Attrition by Salary Band table (conditional formatting) |
| **7. Dashboard — Deep Dive 2** | Attrition by Age Group + Marital Status + Business Travel + Overtime + Education Field |
| **8. Slicers** | Age, Department, Salary Band filters applied across all 3 pages |

---

Key Insights
------------

**Overall KPIs:**

| Metric | Value |
|--------|-------|
| Total Headcount | 1,470 |
| Employees Left | 237 |
| **Attrition Rate** | **16.12%** |
| Average Income | $6,503 |
| Avg Tenure of Leavers | 5.1 years |

**Q1 — What is the overall attrition rate?**

| # | Insight |
|---|---------|
| 1 | Overall attrition rate is **16.12%** — meaning 1 in 6 employees left the organization |
| 2 | **237 employees left** out of a total headcount of 1,470 — with an average tenure of only **5.1 years** |

**Q2 — Which departments are losing the most people?**

| # | Insight |
|---|---------|
| 3 | **Sales has the highest attrition (20.63%)** — 1 in 5 Sales employees left |
| 4 | **Human Resources** follows at 19.05% — a concerning rate for the people function itself |
| 5 | **R&D has the lowest attrition (13.84%)** despite being the largest department with 133 leavers |
| 6 | **Sales Representatives have the highest role-level attrition (39.76%)** — nearly 2 in 5 left (33 out of 83) |
| 7 | **Laboratory Technicians (23.94%)** and **Human Resources role (23.08%)** are next highest risk |
| 8 | **Research Directors (2.50%)** and **Managers (4.90%)** are the most stable roles |

**Q3 — Is there a relationship between pay, age, and the decision to leave?**

| # | Insight |
|---|---------|
| 9 | **YES — pay and attrition are strongly linked.** Under 3K salary band has 28.61% attrition vs only 8.90% for Above 10K |
| 10 | **Attrition drops consistently as salary increases** — pay is the single most controllable retention lever |
| 11 | **YES — age and attrition are strongly linked.** The 18–25 group has the highest attrition (35.77%) |
| 12 | **26–35 group contributes the most leavers (116)** due to large headcount despite lower individual rate (19.14%) |
| 13 | **36–45 age group is the most stable (9.19%)** — mid-career employees are least likely to leave |
| 14 | **Overtime workers are 3x more likely to leave (30.53%)** vs non-overtime employees (10.44%) |
| 15 | **Frequent travelers have 24.91% attrition** — business travel fatigue is a clear retention risk |
| 16 | **Single employees have the highest attrition (25.53%)** vs Married (12.48%) and Divorced (10.09%) |
| 17 | **Technical Degree (24.24%)** and **Human Resources field (25.93%)** have the highest education-based attrition |

---

Dashboard / Output
------------------

**The Power BI dashboard is organized into 3 pages with Age, Department & Salary Band filters on every page:**

### Page 1 — Overview
![Dashboard Page 1](image/page1.png)

| Section | Details |
|---------|---------|
| KPI Cards | Attrition Rate (16.12%) · Employees Left (237) · Total Headcount (1,470) · Average Income (6,503) · Avg Tenure of Leavers (5.1 yrs) |
| Attrition by Department | Bar chart — Sales (20.63%) · HR (19.05%) · R&D (13.84%) |
| Attrition Decomposition | Decomposition tree — Department → Job Role → Salary Band drill-down |

---

### Page 2 — Deep Dive 1
![Dashboard Page 2](image/page2.png)

| Section | Details |
|---------|---------|
| Attrition by Job Role | Table — 9 roles with Total Headcount, Employees Left & color-coded Attrition Rate % |
| Attrition by Salary Band | Table — Under 3K (28.61%) · 3K–6K (12.72%) · 6K–10K (12.00%) · Above 10K (8.90%) with conditional formatting |

---

### Page 3 — Deep Dive 2
![Dashboard Page 3](image/page3.png)

| Section | Details |
|---------|---------|
| Attrition by Age Group | Table — 18–25 (35.77%) · 26–35 (19.14%) · 36–45 (9.19%) · 46–60 (12.45%) |
| Attrition by Marital Status | Donut + Bar chart — Single (25.53%) · Married (12.48%) · Divorced (10.09%) |
| Attrition by Business Travel | Donut — Travel_Frequently (24.91%) · Travel_Rarely (14.96%) · Non-Travel (8.00%) |
| Attrition by Overtime | Bar chart — Yes (30.53%) · No (10.44%) |
| Attrition by Education Field | Table — HR (25.93%) · Technical (24.24%) · Marketing (22.01%) · Life Sciences (14.69%) |

---

How to Run This Project
-----------------------

**Power BI Dashboard**

| Step | Action |
|------|--------|
| 1 | Open **Microsoft Fabric** or **Power BI Desktop** |
| 2 | Load `HR-Employee-Attrition.csv` as data source |
| 3 | Recreate `Age_Group` and `Salary_band` buckets in Power Query |
| 4 | Build DAX measures for Attrition Rate, Employees Left, Avg Tenure |
| 5 | Navigate between Overview → Deep Dive 1 → Deep Dive 2 using top buttons |

> 📥 **Power BI file — Download here:** [Google Drive Link](#) *(update with your link)*

---

Results & Conclusion
====================

The analysis directly answers all 3 business questions:

1. **Overall attrition rate is 16.12%** — 237 out of 1,470 employees left with an average tenure of 5.1 years.
2. **Sales is losing the most people (20.63%)** — followed by HR (19.05%), with Sales Representatives at a critical 39.76% attrition rate.
3. **Yes — both pay and age strongly predict attrition.** Low earners (Under 3K: 28.61%) and young employees (18–25: 35.77%) are the highest-risk segments. Overtime workers (30.53%) and frequent travelers (24.91%) compound the risk further.

**Recommendation:** Prioritize salary increases for Under 3K earners, reduce overtime burden in Sales, and build targeted retention programs for employees aged 18–35.

---

Author & Contact
----------------

| Field | Info |
|-------|------|
| **Name** | *KRISHNA* |
| **LinkedIn** | *https://www.linkedin.com/in/krishna-prajapati-26a106231/* |
| **GitHub** | *https://github.com/* |

---

⭐ *If you found this project helpful, consider giving it a star!*
