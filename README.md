# 🧑‍💼 Analysis of Employee Dataset

## 📑 Table of Contents
1. [Project Overview](#project-overview)  
2. [Data Sources](#data-sources)  
3. [Tools](#tools)  
4. [Data Cleaning/Preparation](#data-cleaningpreparation)  
5. [Exploratory Data Analysis](#exploratory-data-analysis)  
6. [Data Analysis](#data-analysis)  
7. [Results/Findings](#resultsfindings)  
8. [Recommendations](#recommendations)  
9. [Limitations](#limitations)  
10. [References](#references)

---

## 1. 📝 Project Overview
**This project analyzes a comprehensive HR dataset to uncover insights into employee demographics, job roles, salaries, attrition, and other workforce metrics. The goal is to identify trends, potential issues, and opportunities for improving HR strategies, such as retention, compensation, and hiring practices. The analysis aims to provide actionable recommendations for optimizing workforce management in a technology-driven organization.**

**Description:**
Contains 1,469 employee records with attributes including gender, age, department, job role, salary, attrition, years at company, education, and more.

**Structure:**
Multiple sheets/tabs with aggregated pivot tables and raw employee data, including demographic breakdowns, salary averages, and attrition metrics.

**Key Metrics:**
  * Employee demographics (gender, age, ethnicity, marital status)
  * Job roles and departments
  * Salary and overtime data
  * Attrition and tenure
  * Hiring trends and education backgrounds

---

## 2. 📊 Data Sources
* The dataset is sourced from a single Microsoft Excel file:
  * **Employee Table** (`Employee` sheet): Contains demographic, employment, and performance-related information for each employee.
  * **HR Dashboard** (`Dashboard` sheet): A visual report summarizing key HR KPIs like attrition rate, travel frequency, role changes, and more.

---

## 3. 🛠 Tools
- **Microsoft Excel**: For data storage, pivot table creation, and dashboard visualizations.
- **GitHub**: For version control and public sharing of this analysis.

---

## 4. 🧹 Data Cleaning/Preparation
Key preparation steps included:
- Ensuring all date fields were properly formatted (e.g., `HireDate`).
- Handling missing values and duplicates.
- Standardizing text entries (e.g., `Role Status`, `Employee Classification`).
- Categorizing age groups and tenure ranges.
- Creating derived columns like:
  - `YearsAtCompany`, `YearsInMostRecentRole`, `YearsSinceLastPromotion`
  - `Employee Classification` (e.g., Senior vs Long-Serving)
  - `Attrition` (binary categorical variable)

---

## 5. 🔍 Exploratory Data Analysis
Some basic EDA observations:
- Employees are spread across three departments: Sales, Human Resources, and Technology.
- Age ranges vary, with a focus on employees aged 30-40.
- Gender diversity is represented, including Male, Female, and Non-Binary.
- Attrition is recorded along with performance indicators such as overtime, travel frequency, and promotions.

---

## 6. 📈 Data Analysis
Key analysis points based on pivot tables and dashboard visuals:
- **Attrition Breakdown**: Affected more by employees with recent role changes and longer commute distances.
- **Travel Impact**: Employees who travel frequently show higher attrition.
- **Role Stability**: Long-serving employees with "Same Role" status have significantly lower attrition rates.
- **Overtime & Attendance**:
  - 71.9% of employees work on time.
  - 28.0% work overtime — with higher attrition rates.
- **Departmental Distribution**:
  - Sales and Technology have the highest number of employees.
  - Human Resources shows a balanced age and gender representation.

---

## 7. 📊 Results/Findings
- **Attrition Rate** appears strongly linked with:
  - Years with current manager (lower years → higher attrition).
  - Years since last promotion (long gaps → dissatisfaction).
  - Overtime workers are more likely to leave.
- **Travel Requirements** can be a key driver of burnout or turnover.
- Employees in stable roles with longer tenure are more likely to stay.

---

## 8. ✅ Recommendations
- **Review Travel Policies**: Consider reducing travel frequency or offering incentives to frequent travelers.
- **Managerial Development**: Support employee-manager relationship building, especially for new pairings.
- **Targeted Retention**: Focus retention efforts on employees in "Different Role" status or without recent promotions.
- **Optimize Workload**: Limit overtime or provide better compensation to reduce burnout.
- **HR Reporting**: Continue updating the dashboard monthly to monitor trends over time.

---

## 9. ⚠️ Limitations
- **Single Point in Time**: Data represents a snapshot rather than a time-series trend.
- **Missing External Data**: No economic or industry benchmarks are included.

---

## 10. 📚 References
- Dataset: *Employee - Classwork WB.xlsx*
- Visualization Tools: Microsoft Excel PivotTables & Charts
- Dataset Source: Created for classwork purposes (assumed simulated data)
