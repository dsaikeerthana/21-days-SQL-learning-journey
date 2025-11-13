# 📅 Day 10 (13/11): CASE Statements

## 🧩 Overview
Today’s learning covered **CASE statements**, which allow for conditional logic within SQL queries.  
They’re extremely useful for creating categorized outputs, conditional aggregations, and even custom sorting — without needing to modify raw data.

---

## 📘 Topics Covered

| Concept | Description |
|----------|-------------|
| **CASE WHEN ... THEN ... ELSE ... END** | Applies conditional logic within a query. |
| **Derived Columns** | Use CASE to create new computed or labeled columns. |
| **Custom Sorting** | Use CASE in ORDER BY for flexible ranking logic. |
| **Nested CASE** | Embed CASE inside another CASE for complex logic. |
| **Execution Order** | CASE checks conditions top-to-bottom — first match wins. |

---

## ✅ Tips & Tricks

- ✅ Always include **ELSE** to handle unexpected values (avoid NULL results).  
- ✅ **CASE is an expression**, not a statement — can be used anywhere a value is expected.  
- ✅ Combine CASE with **aggregates or string/date functions** for dynamic categorization.  
- ✅ Use **CASE in ORDER BY** for custom sorting logic.  
- ✅ Keep CASE logic simple and readable — nesting is powerful but can become confusing.

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Categorize satisfaction levels
SELECT 
    name,
    satisfaction_score,
    CASE 
        WHEN satisfaction_score >= 90 THEN 'Excellent'
        WHEN satisfaction_score >= 70 THEN 'Good'
        WHEN satisfaction_score >= 50 THEN 'Average'
        ELSE 'Poor'
    END AS satisfaction_level
FROM patients;

-- 2️⃣ Flag services by performance
SELECT 
    service,
    AVG(satisfaction) AS avg_satisfaction,
    CASE 
        WHEN AVG(satisfaction) >= 85 THEN 'High Performing'
        WHEN AVG(satisfaction) BETWEEN 60 AND 84 THEN 'Moderate'
        ELSE 'Needs Improvement'
    END AS performance_category
FROM services_weekly
GROUP BY service;

-- 3️⃣ Custom sort using CASE
SELECT 
    service, 
    total_refused
FROM services_weekly
ORDER BY 
    CASE 
        WHEN total_refused > 200 THEN 1
        WHEN total_refused BETWEEN 100 AND 200 THEN 2
        ELSE 3
    END;

