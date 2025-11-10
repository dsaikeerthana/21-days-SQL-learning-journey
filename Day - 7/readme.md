# 📅 Day 7 (10/11): HAVING Clause

## 🧩 Overview
Today’s learning focused on the **HAVING clause**, which is used to filter aggregated results after applying `GROUP BY`.  
Unlike `WHERE` (which filters raw rows), `HAVING` filters groups—making it essential for analysis and reporting.

---

## 📘 Topics Covered

| Concept | Description |
|---------|-------------|
| **HAVING** | Filters aggregated/grouped results after GROUP BY. |
| **WHERE vs HAVING** | WHERE filters rows (before grouping), HAVING filters groups (after grouping). |
| **Aggregates Allowed** | HAVING supports SUM, COUNT, AVG, MIN, MAX, etc. |
| **Grouping Requirement** | HAVING must be used with GROUP BY. |
| **Multiple Conditions** | Supports AND/OR just like WHERE. |

---

## ✅ Tips & Tricks

- **Execution order**:  
  `WHERE → GROUP BY → HAVING → ORDER BY`
- Use **WHERE for row filtering**, **HAVING for group filtering**.  
- HAVING allows aggregate functions; WHERE cannot use aggregates.  
- Some SQL engines allow alias use in HAVING (MySQL supports this).  
- Combine conditions using AND/OR for complex group-level filtering.

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Groups with total admitted > 200
SELECT 
    service,
    SUM(patients_admitted) AS total_admitted
FROM services_weekly
GROUP BY service
HAVING SUM(patients_admitted) > 200;

-- 2️⃣ Weeks where total staff < 50
SELECT 
    week,
    SUM(staff_presence) AS total_staff
FROM services_weekly
GROUP BY week
HAVING SUM(staff_presence) < 50;

-- 3️⃣ Services with average satisfaction < 75
SELECT 
    service,
    AVG(satisfaction) AS avg_satisfaction
FROM patients
GROUP BY service
HAVING AVG(satisfaction) < 75;

Daily Challenge

Question:

Identify services that refused more than 100 patients in total
and had an average patient satisfaction below 80.
Show: service, total_refused, avg_satisfaction.
