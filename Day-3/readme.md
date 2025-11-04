# 📅 Day 3: Sorting Data with ORDER BY

## 🧩 Overview
After learning how to **filter** data using `WHERE`, today’s focus was on how to **organize and present** it using the `ORDER BY` clause.  
Sorting allows us to view data in a structured, meaningful order — whether it’s alphabetically, numerically, or by date.

---

## 📘 Topics Covered

| Concept | Description |
|----------|-------------|
| **ORDER BY** | Used to sort query results based on one or more columns. |
| **ASC** | Sorts data in ascending order (A → Z, 0 → 9, oldest → newest). This is the default behavior. |
| **DESC** | Sorts data in descending order (Z → A, 9 → 0, newest → oldest). |
| **Multiple Column Sorting** | You can sort by more than one column, e.g. `ORDER BY department ASC, age DESC`. |
| **NULL Handling** | In most SQL engines, `NULL` values appear **first** when sorting ascending and **last** when sorting descending. |
| **Top N Queries** | Combine `ORDER BY ... DESC` with `LIMIT` to fetch the top results, such as top-performing departments or lowest satisfaction scores. |

---

## 🧠 Key Insight
Sorting is more than just arranging data — it’s about **prioritizing information**.  
For analysts, it helps highlight extremes (top performers or problem areas) and makes reports far easier to interpret.  

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Sort patients by name (alphabetical order)
SELECT patient_id, name, age
FROM patients
ORDER BY name ASC;

-- 2️⃣ Sort by satisfaction score from highest to lowest
SELECT name, satisfaction_score
FROM patients
ORDER BY satisfaction_score DESC;

-- 3️⃣ Sort by department (A-Z), then by satisfaction score (highest first)
SELECT department, name, satisfaction_score
FROM patients
ORDER BY department ASC, satisfaction_score DESC;


Daily Challenge

Question:

Retrieve the top 5 weeks with the highest patient refusals across all services, showing week, service, patients_refused, and patients_request.
Sort the results by patients_refused in descending order.
