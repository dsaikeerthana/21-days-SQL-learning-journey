# 📅 Day 2 (04/11): Filtering Data with WHERE Clause

## 🧩 Overview
Today’s focus was on one of the most powerful SQL commands — the `WHERE` clause.  
If `SELECT` helps us *view* data, `WHERE` helps us *focus* on what really matters.  
It’s like setting filters in a spreadsheet — but far more flexible and precise.

---

## 📘 Topics Covered

| Concept | Description |
|----------|-------------|
| **WHERE** | Filters records that meet specific conditions. |
| **Comparison Operators** (`=`, `<`, `>`, `<=`, `>=`, `!=`) | Used to compare column values with constants or other columns. |
| **Logical Operators** (`AND`, `OR`, `NOT`) | Combine multiple conditions to create complex filters. |
| **BETWEEN / NOT BETWEEN** | Filters data within or outside a specific numeric or date range. |
| **IN / NOT IN** | Matches values from a defined list of options. |
| **LIKE / NOT LIKE** | Performs pattern matching using wildcards (`%`, `_`). |
| **IS NULL / IS NOT NULL** | Checks for missing (NULL) or present values. |
| **COALESCE()** | Returns the first non-NULL value from a list of expressions. |
| **ISNULL()** | Replaces NULL with a specified value (database-specific). |
| **NULLIF()** | Returns NULL if two expressions are equal, otherwise returns the first expression. |

---

## 🧠 Key Insight
Filtering is the **core of SQL data analysis**.  
It allows you to move from “viewing everything” to “focusing on what’s relevant.”  
With proper filtering, we can detect patterns, outliers, and trends that drive business decisions.

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Patients older than 60
SELECT * 
FROM patients
WHERE age > 60;

-- 2️⃣ Patients from Cardiology with satisfaction above 80
SELECT patient_id, name, satisfaction_score
FROM patients
WHERE department = 'Cardiology' AND satisfaction_score > 80;

-- 3️⃣ Records where phone number is missing
SELECT name, contact_number
FROM patients


Daily Challenge

Question:

Find all patients admitted to the 'Surgery' service with a satisfaction score below 70,
showing their patient_id, name, age, and satisfaction_score.
WHERE contact_number IS NULL;

