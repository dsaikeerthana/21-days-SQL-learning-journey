
# 📅 Day 11: DISTINCT and Handling Duplicates

## 🧩 Overview
Today’s learning focused on the **DISTINCT** keyword — one of the simplest yet most powerful SQL tools for ensuring data uniqueness and removing duplicates.  
It’s especially important when cleaning datasets, preparing summaries, or validating data integrity.

---

## 📘 Topics Covered

| Concept | Description |
|----------|-------------|
| **DISTINCT** | Removes duplicate rows from the result set. |
| **Unique Combinations** | DISTINCT considers all selected columns together. |
| **COUNT(DISTINCT column)** | Counts unique non-NULL values in a column. |
| **DISTINCT vs GROUP BY** | DISTINCT removes duplicates; GROUP BY aggregates data. |
| **NULL Handling** | All NULLs are treated as equal — only one NULL is returned. |
| **Performance** | DISTINCT can be expensive on large datasets — use wisely. |

---

## ⚙️ Key Notes

✅ **DISTINCT** applies to the *entire row*, not individual columns.  
✅ **COUNT(DISTINCT column)** helps identify unique values in metrics.  
✅ **DISTINCT with NULL** — only one NULL appears.  
✅ **Performance tip:** Remove duplicates during data preprocessing when possible.  
✅ Use **GROUP BY** if you also need aggregations (like SUM, COUNT, AVG).  

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Retrieve unique services
SELECT DISTINCT service
FROM services_weekly;

-- 2️⃣ Find unique service-week combinations
SELECT DISTINCT service, week
FROM services_weekly;

-- 3️⃣ Count total distinct services offered
SELECT COUNT(DISTINCT service) AS unique_services
FROM services_weekly;

-- 4️⃣ Distinct patient names with non-NULL values
SELECT DISTINCT name
FROM patients
WHERE name IS NOT NULL;

-- 5️⃣ Using GROUP BY instead of DISTINCT
SELECT service
FROM services_weekly
GROUP BY service;

Question: Find all unique combinations of service and event type from
the services_weekly table where events are not null or none, along with
the count of occurrences for each combination. Order by count descending.
