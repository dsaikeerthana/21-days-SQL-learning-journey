# 📅 Day 9 (12/11): Date Functions

## 🧩 Overview
Today’s session covered **Date Functions** — the foundation for handling time-based data in SQL.  
Whether it’s tracking events, calculating durations, or extracting year/month details, mastering date functions helps unlock powerful time-based analysis.

---

## 📘 Topics Covered

| Function | Description |
|----------|-------------|
| **CURRENT_DATE / NOW()** | Returns the current date or timestamp. |
| **DATE()** | Extracts date part from a timestamp or datetime. |
| **EXTRACT() / DATEPART()** | Extracts a specific component (year, month, day, etc.). |
| **YEAR(), MONTH(), DAY()** | Simpler ways to get specific parts of a date. |
| **DATEDIFF(date1, date2)** | Returns the difference between two dates (in days). |
| **DATE_ADD(date, INTERVAL n DAY)** | Adds n days to a date. |
| **DATE_SUB(date, INTERVAL n DAY)** | Subtracts n days from a date. |
| **STR_TO_DATE(string, format)** | Converts a string into a date (MySQL). |
| **TO_DATE(string, format)** | Converts a string into a date (PostgreSQL, Oracle). |
| **CAST() / CONVERT()** | Converts a column into a date type for comparisons. |

---

## ⚙️ Best Practices

✅ **Avoid using date functions directly in WHERE** — they can make queries slower by preventing index usage.  
✅ **Cast or convert** date calculations to proper types (`INTEGER`, `REAL`, or `DATE`) for consistency.  
✅ **Precompute year/month fields** in large datasets to optimize performance.  
✅ Always maintain consistent date formats (especially when importing from CSV or Excel).

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Get today’s date
SELECT CURRENT_DATE AS today;

-- 2️⃣ Extract year and month from admission_date
SELECT 
    EXTRACT(YEAR FROM admission_date) AS year,
    EXTRACT(MONTH FROM admission_date) AS month
FROM patients;

-- 3️⃣ Calculate number of days since admission
SELECT 
    patient_id,
    DATEDIFF(CURRENT_DATE, admission_date) AS days_since_admission
FROM patients;

-- 4️⃣ Add 7 days to a date
SELECT 
    DATE_ADD(admission_date, INTERVAL 7 DAY) AS follow_up_date
FROM patients;

-- 5️⃣ Convert a string to a date
SELECT 
    STR_TO_DATE('2025-11-12', '%Y-%m-%d') AS formatted_date;

### Daily Challenge:

**Question:** Calculate the average length of stay (in days) for each service, showing only services where the average stay is more than 7 days. Also show the count of patients and order by average stay descending.
