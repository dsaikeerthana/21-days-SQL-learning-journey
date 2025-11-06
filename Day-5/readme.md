# 📅 Day 5 (07/11): Aggregate Functions (COUNT, SUM, AVG, MIN, MAX)

## 🧩 Overview
Today’s topic centered on **aggregate functions**, which allow us to summarize and analyze data across multiple rows.  
These functions are essential for reporting, dashboards, and high-level analysis.

---

## 📘 Topics Covered

| Function | Description |
|----------|-------------|
| **COUNT(*)** | Counts **all rows**, including rows with NULL values. |
| **COUNT(column)** | Counts only **non-NULL** values in a column. |
| **SUM(column)** | Calculates the total sum of numeric values. |
| **AVG(column)** | Finds the average of numeric values (ignores NULLs). |
| **MIN(column)** | Returns the smallest value. |
| **MAX(column)** | Returns the largest value. |

✅ **Aggregates ignore NULLs** (except `COUNT(*)`).  
✅ Always **alias** your aggregates for better clarity.

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Total number of patients
SELECT COUNT(*) AS total_patients
FROM patients;

-- 2️⃣ Average satisfaction score
SELECT AVG(satisfaction) AS avg_satisfaction
FROM patients;

-- 3️⃣ Highest and lowest satisfaction
SELECT 
    MAX(satisfaction) AS highest_satisfaction,
    MIN(satisfaction) AS lowest_satisfaction
FROM patients;

-- 4️⃣ Using multiple aggregates together
SELECT 
    COUNT(*) AS total_patients,
    SUM(patients_refused) AS total_refusals,
    ROUND(AVG(satisfaction), 2) AS avg_satisfaction
FROM services_weekly;

Daily Challenge

Question:

Calculate the total number of patients admitted, total patients refused, and the average patient satisfaction across all services and weeks.
Round the average satisfaction to 2 decimal places.
