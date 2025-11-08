# 📅 Day 6: GROUP BY Clause

## 🧩 Overview
Today’s focus was the **GROUP BY** clause, which allows us to aggregate data by categories — such as services, departments, or weeks.  
It’s one of the most essential SQL tools for building summaries and analytics.

---

## 📘 Topics Covered

| Concept | Description |
|---------|-------------|
| **GROUP BY** | Groups rows with the same column values so aggregates apply to each group. |
| **Aggregates per group** | Apply COUNT, SUM, AVG, MIN, MAX to each group. |
| **Rules** | Non-aggregated columns must be included in GROUP BY. Groups return one row. |
| **WHERE vs HAVING** | WHERE filters before grouping; HAVING filters groups after aggregation. |
| **Multiple Grouping** | Group by multiple columns for finer breakdowns. |
| **Ordering Aggregates** | You can ORDER BY aggregated results. |

---

## ✅ Tips & Tricks

- **Think “one row per group”.**  
- Execution order:  
  `FROM → WHERE → GROUP BY → SELECT → ORDER BY → LIMIT`  
- Use **WHERE** to filter raw rows; use **HAVING** to filter aggregated groups.  
- Alias aggregates for readability in SELECT and ORDER BY.  
- Group by multiple columns for deeper insights.

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Group by service: total patients admitted
SELECT 
    service,
    COUNT(*) AS total_admitted
FROM patients
GROUP BY service;

-- 2️⃣ Group by service: average satisfaction
SELECT 
    service,
    AVG(satisfaction) AS avg_satisfaction
FROM patients
GROUP BY service;

-- 3️⃣ Group by service and week
SELECT 
    service,
    week,
    SUM(patients_requested) AS total_requests
FROM services_weekly
GROUP BY service, week;

💪 Daily Challenge

Question:
For each hospital service, calculate:
Total patients admitted
Total patients refused
Admission rate (% of requests admitted)
Order results by admission rate (DESC).
