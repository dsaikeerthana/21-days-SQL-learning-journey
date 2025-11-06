# 📅 Day 4: LIMIT and OFFSET

## 🧩 Overview
Today’s learning focused on **LIMIT** and **OFFSET**, which help control how many rows are displayed and from where the data retrieval should begin.  
These are the foundation of **pagination**, widely used in web apps, dashboards, and reports.

---

## 📘 Topics Covered

| Concept | Description |
|--------|-------------|
| **LIMIT** | Restricts the number of rows returned. Useful for top results or previewing data. |
| **OFFSET** | Skips a specified number of rows before starting to return results. |
| **Pagination** | Combining LIMIT + OFFSET to navigate through data in chunks (pages). |

---

## 🧠 Key Insight
LIMIT and OFFSET make it efficient to work with large tables.  
Instead of pulling thousands of rows at once, you can retrieve only what you need — improving both performance and usability.

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Get the first 10 patients
SELECT *
FROM patients
LIMIT 10;

-- 2️⃣ Skip the first 20 rows and return the next 10
SELECT *
FROM patients
LIMIT 10 OFFSET 20;

-- 3️⃣ Pagination example: Page 3 with 15 rows per page
-- Page 3 starts after 30 rows (15 * 2)
SELECT *
FROM patients
LIMIT 15 OFFSET 30;

𝐃𝐚𝐢𝐥𝐲 𝐂𝐡𝐚𝐥𝐥𝐞𝐧𝐠𝐞
𝐐𝐮𝐞𝐬𝐭𝐢𝐨𝐧:
Find the 3rd to 7th highest patient satisfaction scores from the patients table, showing patient_id, name, service, and satisfaction. Display only these 5 records.
