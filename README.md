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

![HR dashboard Image](https://github.com/user-attachments/assets/00720b3a-2e1f-4e56-a4b2-d80b1bf8ac24)

---

## 2. 📊 Data Sources
* The dataset is sourced from a single Microsoft Excel file created for practice purposes:
  * **Employee Table** (`Employee` sheet): Contains demographic, employment, and performance-related information for each employee.
---

## 3. 🛠 Tools
- **Microsoft Excel**: For data storage, pivot table creation, and dashboard visualizations.
- **GitHub**: For version control and public sharing of this analysis.
---

## 4. 🧹 Data Cleaning/Preparation
### Key preparation steps included:
- Data Standardization:
  - Converted date fields (e.g., `HireDate`) to a readable format (e.g., month names, quarters) where needed.
  - Corrected formatting for non-date fields like `Salary` to ensure numerical consistency (e.g., removed any text or symbols).
  - Ensured consistent naming conventions (e.g., `Female` vs. `F` not present).
  - Categorized employees into age groups and tenure ranges for analysis.
- Creating Derived Columns:
  - Created `FullName` by concatenating `FirstName` and `LastName` using the Excel formula:
       ```excel
       =[@FirstName]&" "&[@LastName]
       ```
  - Created `Age Group`, `Distance Group`, and `Employee Classification` using nested IF Excel functions:
     ```excel
     =IF([@Age]<30,"<30",IF([@Age]<=40,"30-40",">40"))
     ```
     ```excel
     =IF([@[DistanceFromHome (KM)]]<=5,"Close",IF([@[DistanceFromHome (KM)]]<=15,"FAR","Very Far"))
     ```
     ```excel
     =IF([@YearsAtCompany]<=2,"Junior Employee",IF([@YearsAtCompany]<=5,"Mid-Tenure Employee",IF([@YearsAtCompany]<=7,"Senior Employee","Long-Serving Employee")))
     ```
  - Created `Role Status` (indicating 'Different Role' or 'Same Role') using the IF function:
   ```excel
     =IF([@YearsAtCompany]=[@YearsInMostRecentRole],"Same Role","Different Role")
   ```
- Handling missing values and duplicates:
  - Confirmed no duplicate EmployeeIDs in the raw data.
- Data Aggregation:
  - Generated pivot table summaries for key metrics (e.g., gender counts, average salaries) using standardized data.
  - Grouped data by categories such as department, job role, and education level for detailed analysis.
  - Created plots and charts based on pivot table summaries to visualize trends and patterns.
---

## 5. 🔍 Exploratory Data Analysis
Exploratory Data Analysis (EDA) was conducted to understand the dataset's structure and identify patterns. 
Key areas explored include:
### Employee Demographics
- **Total Employees**: 1,469
- **Gender Distribution**:
  - Female: 674 (45.88%)
  - Male: 651 (44.31%)
  - Non-Binary: 124 (8.44%)
  - Prefer Not To Say: 20 (1.36%)
- **Age**:
  - Average Age: 28.99 years
  - Age Groups:
    - `Less than 30` < 30: 955 (65.01%)
    - `Between 30 and 40` 30-40: 321 (21.85%)
    - `Greater than 40` > 40: 193 (13.14%)
- **Ethnicity**:
  - White: 859 (58.48%)
  - Black or African American: 207 (14.09%)
  - Mixed or Multiple Ethnic Groups: 198 (13.48%)
  - Asian or Asian American: 113 (7.69%)
  - American Indian or Alaska Native: 50 (3.40%)
  - Native Hawaiian: 26 (1.77%)
  - Other: 16 (1.09%)
- **Marital Status**:
  - Married: 624 (42.48%)
  - Single: 549 (37.37%)
  - Divorced: 296 (20.15%)
- **State of Residence**:
  - California (CA): 875 (59.56%)
  - New York (NY): 419 (28.52%)
  - Illinois (IL): 175 (11.92%)

The workforce is relatively young, with a majority under 30 years old. Gender distribution is fairly balanced, though non-binary and "prefer not to say" categories are small. The majority of employees are White, and California is the dominant state of residence, likely indicating key operational hubs.

---
### Department and Job Roles
- **Departments**:
  - Technology: 961 employees (65.42%)
  - Sales: 445 employees (30.29%)
  - Human Resources: 63 employees (4.29%)
- **Job Roles** (Top 5 by Count):
  - Sales Executive: 326 (28.13% of total roles)
  - Software Engineer: 294 (25.37%)
  - Data Scientist: 261 (22.52%)
  - Machine Learning Engineer: 146 (12.60%)
  - Senior Software Engineer: 132 (11.39%)
- **Average Salary by Department**:
  - Human Resources: $119,698.81
  - Sales: $119,155.94
  - Technology: $109,655.12
- **Average Salary by Job Role** (Top 5):
  - HR Manager: $449,330.75
  - Analytics Manager: $346,484.23
  - Manager: $317,531.05
  - HR Business Partner: $314,002.43
  - Engineering Manager: $286,258.51

The Technology department dominates in headcount, reflecting a tech-heavy organization. Sales Executives and Software Engineers are the most common roles. High-paying roles like HR Manager and Analytics Manager indicate specialized positions command premium salaries. Technology roles, despite being numerous, have lower average salaries compared to HR and Sales.

---
### Salary Analysis
- **Overall Average Salary**: $112,963.92
- **Salary by Gender**:
  - Female: $113,953.31
  - Male: $111,773.81
  - Non-Binary: $111,395.51
  - Prefer Not To Say: $128,083.35
- **Salary by Education Level**:
  - Level 1: $94,983.48
  - Level 2: $105,180.54
  - Level 3: $115,405.43
  - Level 4: $117,641.06
  - Level 5: $155,379.64
- **Salary by Education Field** (Top Fields by Count):
  - Computer Science (440 employees): No salary data provided per field
  - Information Systems (363 employees)
  - Marketing (166 employees)
  - Economics (101 employees)
- **Overtime Impact**:
  - Employees working overtime (416): Average salary $112,963.92 (same as overall, suggesting no direct salary premium for overtime)
  - Non-overtime employees (1,053): Same average salary

Salaries are relatively equitable across genders, with "Prefer Not To Say" employees earning the highest average. Higher education levels correlate strongly with higher salaries, with Level 5 earning significantly more. Overtime does not appear to directly increase average salary, possibly indicating hourly vs. salaried roles or fixed compensation structures.

---
### Attrition Analysis
- **Attrition Rate**:
  - No Attrition: 1,232 (83.87%)
  - Attrition: 237 (16.13%)
- **Attrition by Gender**:
  - Female: 15.43%
  - Male: 17.51%
  - Non-Binary: 15.32%
  - Prefer Not To Say: 0%
- **Attrition by Department**:
  - Human Resources: 63 employees (no specific attrition rate provided)
  - Sales: 445 employees
  - Technology: 961 employees
- **Average Age by Attrition**:
  - No Attrition: 29.46 years
  - Attrition: 26.54 years
- **Average Years at Company**:
  - No Attrition: 4.97 years
  - Attrition: 2.43 years
- **Distance from Home**:
  - No Attrition: 22.55 km
  - Attrition: 22.22 km (minimal difference)

Attrition is relatively low at 16.13%, with males showing slightly higher turnover than females. Younger employees and those with shorter tenure are more likely to leave. Distance from home does not significantly impact attrition. The "Prefer Not To Say" group has no attrition, possibly due to its small sample size.

---
### Tenure and Promotions
- **Average Years at Company**: 4.56 years
  - By Department:
    - Technology: 4.61 years
    - Human Resources: 4.46 years
    - Sales: 4.46 years
- **Average Years Since Last Promotion**: 3.44 years
- **Employee Classification**:
  - Long-Serving Employee: 9.02 years, $141,223.55 average salary
  - Senior Employee: 6.55 years, $93,753.00
  - Mid-Tenure Employee: 3.92 years, $103,119.87
  - Junior Employee: 0.87 years, $108,558.99
- **Years in Most Recent Role**: 2.29 years (overall)
- **Years with Current Manager**: 2.24 years (overall)

Tenure is moderate, with Technology employees staying slightly longer. Long-serving employees earn significantly more, reflecting seniority-based compensation. The average time since the last promotion (3.44 years) suggests promotion cycles may be slow, potentially contributing to attrition among younger employees.

---
### Hiring Trends
- **Hire Dates** (by Quarter):
  - Q1 (Jan-Mar): 408 hires (27.77%)
  - Q2 (Apr-Jun): 391 hires (26.62%)
  - Q3 (Jul-Sep): 336 hires (22.87%)
  - Q4 (Oct-Dec): 334 hires (22.74%)
- **Hire by Month** (Top Months):
  - March: 153 hires
  - May: 140 hires
  - April: 135 hires
- **Hire by Day of Week**:
  - Tuesday: 230 hires
  - Monday: 226 hires
  - Wednesday: 222 hires
- **Education Field of Hires**:
  - Computer Science: 440
  - Information Systems: 363
  - Marketing: 166

Hiring is fairly evenly distributed across quarters, with a slight peak in Q1. March and May are the most active hiring months, possibly aligning with fiscal or academic cycles. Tuesday is the most common hiring day, suggesting structured onboarding processes. Computer Science and Information Systems dominate educational backgrounds, aligning with the Technology department’s size.

---
### Overtime and Work Patterns
- **Overtime**:
  - Yes: 416 employees (28.32%)
  - No: 1,053 employees (71.68%)
- **Overtime by Job Role** (Count):
  - Sales Executive: 326
  - Software Engineer: 294
  - Data Scientist: 261
- **Average Salary with Overtime**:
  - Same as overall ($112,963.92), indicating no direct correlation with higher pay
- **Business Travel** (from individual records):
  - Some Travel: Most common
  - Frequent Traveller: Present but less common
  - No Travel: Least common

Overtime is common among key roles like Sales Executives and Software Engineers, but it doesn’t translate to higher average salaries, possibly due to salaried positions. Travel requirements vary, with "Some Travel" being the norm, potentially impacting work-life balance.

---
### Role Status and Career Mobility
- **Role Status**:
  - Different Role: 1,022 employees (69.57%)
  - Same Role: 447 employees (30.43%)
- **Average Salary by Role Status**:
  - Not explicitly provided, but inferred from job role salaries
- **Years in Most Recent Role**:
  - Long-Serving: 4.65 years
  - Senior: 3.28 years
  - Mid-Tenure: 1.95 years
  - Junior: 0.37 years

A majority of employees have changed roles, indicating internal mobility or job rotation. Long-serving employees spend significantly more time in their roles, suggesting stability at senior levels. Junior employees change roles quickly, possibly due to early-career exploration or turnover.

---

## 6. 📈 Data Analysis
The following questions were addressed during the analysis:

### What is the demographic profile of the workforce?

The workforce is young (average age 28.99), with 65% under 30. Gender is balanced (46% female, 44% male), but non-binary (8%) and "prefer not to say" (1%) groups are smaller. White employees dominate (58%), and California is the primary location (60%).

### How does salary vary across departments, roles, and demographics?

Human Resources has the highest average salary ($119,698.81), followed by Sales ($119,155.94) and Technology ($109,655.12). Top-paying roles include HR Manager ($449,330.75) and Analytics Manager ($346,484.23). Females earn slightly more ($113,953.31) than males ($111,773.81). Higher education levels (Level 5: $155,379.64) correlate with higher salaries.

### What are the attrition trends?

Attrition is 16.13%, with males (17.51%) slightly higher than females (15.43%). Younger employees (26.54 years) and those with shorter tenure (2.43 years) are more likely to leave. Distance from home has minimal impact (22.22 km vs. 22.55 km).

### What are the hiring and tenure patterns?

Hiring is evenly distributed across quarters, with peaks in March (153 hires) and May (140). Technology roles dominate (65%), with Computer Science (440) as the top education field. Average tenure is 4.56 years, with long-serving employees (9.02 years) earning more ($141,223.55).

### How does overtime affect salaries and roles?

28% of employees (416) work overtime, primarily in Sales Executive and Software Engineer roles. Overtime does not increase average salary ($112,963.92), suggesting salaried positions or fixed compensation.

**Interesting Fact**:
- **Unexpected Finding**: Sales Representatives have the lowest average salary ($40,656.42) but a high attrition rate (16.13% overall, with Sales having 445 employees), suggesting potential dissatisfaction due to compensation relative to workload.

**Key analysis points based on pivot tables and dashboard visuals:**
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
### Key Observations
- **Attrition**:
  - Technology has the highest employee count (961) but a lower attrition rate (16.13% overall).
  - Sales has a higher attrition rate, possibly linked to lower salaries for roles like Sales Representative.
  - Younger employees (<30) have a higher attrition rate (26.54 years average age for Yes vs. 29.46 for No).
- **Salary Insights**:
  - HR Manager and Analytics Manager roles have significantly higher salaries ($449,330.75 and $346,484.23, respectively), indicating specialized or leadership roles.
  - Software Engineers and Data Scientists have lower salaries ($51,967.05 and $56,079.49), despite high demand in Technology.
- **Department Trends**:
  - Technology employees have slightly longer tenure (4.61 years) than Sales (4.46 years) and HR (4.46 years).
  - HR has the highest average salary ($119,698.81), followed by Sales ($119,155.94) and Technology ($109,655.12).
- **Hiring Patterns**:
  - Q1 and Q2 account for 54.73% of hires, with March being the peak month (153 hires).
  - Tuesday and Monday are the most common hiring days (230 and 226 hires).
- **Demographic Distribution**:
  - Females earn slightly higher salaries ($113,953.31) than males ($111,773.81).
  - White employees dominate (58.48%), followed by Black or African American (14.09%).
- **Attrition Rate** appears strongly linked with:
  - Years with current manager (lower years ==> higher attrition).
  - Years since last promotion (long gaps ==> dissatisfaction).
  - Overtime workers are more likely to leave.
- **Travel Requirements** can be a key driver of burnout or turnover.
- Employees in stable roles with longer tenure are more likely to stay.
- **Overtime**:
  - The lack of salary differentiation for overtime workers suggests potential inequities for hourly staff. 
- **Promotion Cycles**:
  - The 3.44-year average since the last promotion may be too long for younger employees, contributing to attrition. 
---
### Conclusion
  - The dataset reveals a young, tech-heavy workforce with moderate attrition and equitable gender-based salaries.
  - Key challenges include retaining younger employees, addressing slow promotion cycles, and ensuring fair compensation for overtime.
  - Strategic recommendations include accelerating promotions, diversifying hiring, and reviewing geographic concentration.
  - The organization is well-positioned but can enhance retention and equity with targeted HR interventions.
---

## 8. ✅ Recommendations
* **Reduce Attrition in Sales**:
   - Increase salaries for Sales Representatives or offer performance-based incentives to improve retention.
   - Implement mentorship programs for younger employees (<30) to enhance engagement.
   - Accelerate promotion reviews for high performers.
* **Optimize Hiring**:
   - Focus hiring efforts in Q1 and Q2 to align with peak hiring months.
   - Target diverse candidates to balance ethnicity representation, especially in Technology.
* **Compensation Review**:
   - Review salary structures for Software Engineers and Data Scientists to ensure competitiveness in the tech industry.
   - Address salary disparities in high-paying roles (e.g., HR Manager) to ensure fairness.
* **Overtime Management**:
   - Investigate overtime prevalence in Sales and Technology to prevent burnout.
   - Offer flexible work arrangements for roles with high overtime (e.g., Sales Representative).
   - Review overtime policies to ensure fair compensation or workload distribution.
* **Dashboard Deployment**:
   - Deploy HR Management Dashboard and continue updating the dashboard monthly to monitor trends over time.
   - Ensure the dashboard is interactive, with filters for department, job role, and attrition status.
---

## 9. ⚠️ Limitations
- **Data Gaps**: The dataset lacks performance metrics (e.g., employee performance ratings), which could enhance attrition analysis.
- **Missing External Data**: No economic or industry benchmarks are included.
- **Sample Size**: Small sample sizes for certain groups (e.g., Prefer Not To Say: 20 employees) limit statistical significance.

---

## 10. 📚 References
- Dataset: *Employee - Practice WB.xlsx*
- Visualization Tools: Microsoft Excel PivotTables & Charts
