# Education-Enrollment-Analysis
A data cleaning and exploratory analysis project on raw education enrollment data, built with Python (pandas, NumPy, Matplotlib) in a Jupyter Notebook.
## 📌Project Overview
The dataset contains student enrollments across multiple courses, branches and instructors. The goal is to clean the messy raw data and answer key business questions about revenue, attendance, dropouts and instructor/branch performance.
## 🗂️ Dataset

**File:** `education_enrollment_raw.csv` (raw, uncleaned enrollment records)

| Column | Description |
|---|---|
| `EnrollmentID` | Unique ID of each enrollment |
| `StudentID` | Unique ID of the student |
| `StudentAge` | Age of the student |
| `StudentGender` | Gender of the student |
| `Branch` | Branch where the student enrolled |
| `Course` | Course name |
| `Instructor` | Instructor teaching the course |
| `CourseFee` | Fee charged for the course |
| `EnrollDate` | Date of enrollment |
| `AttendancePercent` | Percentage of classes attended |
| `FinalScore` | Final score of the student |
| `PaymentStatus` | Payment status of the enrollment |
| `CompletionStatus` | Completed / Dropped / other status |

**Data quality issues found in the raw data:** duplicate rows, extra spaces, inconsistent capitalisation, mixed date formats, impossible ages, negative course fees, attendance above 100%, and missing values in several columns.
## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **Python** | Core programming language |
| **pandas** | Data loading, cleaning, grouping and aggregation |
| **NumPy** | Handling missing and invalid values |
| **Matplotlib** | Charts and visualizations |
| **Jupyter Notebook** | Writing and presenting the analysis |
## 💼 Business Problem

A training institute offers many courses across several branches and instructors. Its raw enrollment records are messy, with duplicates, missing values, wrong entries and inconsistent text, so management cannot easily see what is working and what is not.

This project cleans the data and answers four questions:

1. **Which courses generate the most revenue, and which have the highest enrollment?**
2. **Does attendance affect students' final scores?**
3. **Which courses have the highest dropout risk, and is there a pattern?**
4. **Are any instructors or branches under- or over-performing on completion rate?**

---
## 🧹 Data Cleaning

| Issue | Fix Applied |
|---|---|
| Duplicate rows | Removed with `drop_duplicates()` |
| Extra spaces in IDs, `Branch`, `PaymentStatus` | Trimmed with `.str.strip()` |
| Inconsistent capitalisation | Standardised with `.str.title()` |
| Mixed date formats in `EnrollDate` | Converted with `pd.to_datetime(format="mixed")` |
| Impossible ages (below 10 or above 110) | Set to missing, then filled with the **median** |
| Missing gender, branch, payment status | Filled with `"Unknown"` |
| Negative `CourseFee` | Converted to positive with `.abs()` |
| Missing `CourseFee` | Filled with the **median fee of the same course** |
| Attendance above 100% | Capped at **100** |
| Missing attendance | Filled with the **median** |

## 🔍 Analysis Performed

- **Revenue and enrollment analysis:** grouped by course to compare total revenue and enrollment count
- **Correlation analysis:** measured the relationship between attendance and final score
- **Dropout analysis:** calculated the dropout rate per course and compared average attendance of completed vs. dropped students
- **Performance analysis:** compared completion rates across instructors and branches

---
## 📊 Key Findings

### 1️⃣ Revenue vs. Enrollment
- **Web Development Bootcamp** is the top revenue driver, followed by **Machine Learning Basics**. Both are premium-priced.
- **Spoken English Mastery** has the **highest enrollment (121)** but ranks near the bottom in revenue because it is priced low.
- 👉 **Pricing strategy matters more than popularity for revenue.**

### 2️⃣ Attendance and Final Score
- Correlation of **0.798**, a strong positive relationship.
- 👉 Students who attend more classes score meaningfully higher.

### 3️⃣ Dropout Risk
- About **20%** of all enrollments end in dropout.
- **Data Analytics with Excel** and **Advanced Excel & Power BI** have the highest dropout rates (**about 25-26%**).
- Average attendance is nearly the same for completed (**74.5%**) and dropped (**73.2%**) students.
- 👉 Attendance alone does not explain dropouts. Course difficulty, pacing or teaching should be investigated.

### 4️⃣ Instructor and Branch Performance
- There is a **~10-point completion gap** between the best instructor (**Ms. Iyer, 61.5%**) and the weakest (**Mr. Khan, 51.9%**).
- Branches are close together (**53-59%**), so location is not the main problem.
- The "Unknown" branch has the lowest completion, but that is a data-quality artifact and should be excluded from branch rankings.

---

## 💡 Recommendations

1. **Review pricing** of high-enrollment, low-revenue courses such as Spoken English Mastery.
2. **Promote premium courses** (Web Development, Machine Learning) that drive the most revenue.
3. **Investigate the two Excel courses** with the highest dropout: content difficulty, pacing and support.
4. **Share best practices** from top-performing instructors with the rest of the team.
5. **Encourage attendance**, since it is strongly linked with better scores.
6. **Fix branch data entry** so the "Unknown" branch does not distort reporting.

---

## 📈 Visualizations

The notebook includes:

- 📊 Course revenue (horizontal bar chart)
   ![Revenue by Course](https://github.com/beheramanas0929-dev/Education-Enrollment-Analysis/blob/main/Charts/Revenue%20by%20Course.png)
- 🔵 Attendance % vs. final score (scatter plot)
  ![Attendance % vs. Final Score](https://github.com/beheramanas0929-dev/Education-Enrollment-Analysis/blob/main/Charts/Attendence%25%20VS%20Final%20Score.png)
- 📉 Dropout rate by course (horizontal bar chart)
   ![Dropout Rate by Course](https://github.com/beheramanas0929-dev/Education-Enrollment-Analysis/blob/main/Charts/Dropout%20Rate%20by%20Course.png)
- 🔵 Overall completion status (pie chart)
  
    ![Overall Completion Status](https://github.com/beheramanas0929-dev/Education-Enrollment-Analysis/blob/main/Charts/Completion%20Status%20.png)
                      
 ## 👤 Author

**Manas Behera**

⭐ If you found this project useful, please give it a star!
