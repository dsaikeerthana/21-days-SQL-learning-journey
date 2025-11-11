
# 📅 Day 8 (11/11): String Functions

## 🧩 Overview
Today’s learning focused on **string functions**, which help clean, format, and manipulate text data.  
These functions are essential for preparing messy inputs, standardizing values, or extracting information from text fields.

---

## 📘 Topics Covered

| Function | Description |
|----------|-------------|
| **UPPER()** | Converts text to uppercase. |
| **LOWER()** | Converts text to lowercase. |
| **LENGTH()** | Counts number of characters. |
| **CONCAT() / \|\|** | Joins strings together (DB-dependent). |
| **SUBSTRING()** | Extracts part of a string. |
| **LTRIM() / RTRIM() / TRIM()** | Removes spaces from left, right, or both sides. |

---

## ✅ Tips & Tricks

- Use string functions freely in **SELECT**, but avoid using them in **WHERE** because they prevent index usage and reduce performance.  
- Combine string functions with **CASE** for advanced logic.  
- TRIM is extremely useful when working with raw or imported data containing inconsistent whitespace.  
- Use CONCAT or `||` depending on the database (MySQL uses `CONCAT()`).

---

## 🧪 Practice Examples

```sql
-- 1️⃣ Standardize names to uppercase
SELECT UPPER(name) AS name_upper
FROM patients;

-- 2️⃣ Remove extra spaces from service names
SELECT TRIM(service) AS clean_service
FROM patients;

-- 3️⃣ Extract first 3 letters of service code
SELECT SUBSTRING(service_code, 1, 3) AS service_prefix
FROM services_weekly;

-- 4️⃣ Combine fields using CONCAT
SELECT CONCAT(first_name, ' ', last_name) AS full_name
FROM patients;

-- 5️⃣ Length of phone numbers
SELECT name, LENGTH(phone_number) AS phone_length
FROM patients;

### Daily Challenge:

**Question:** Create a patient summary that shows patient_id, full name in uppercase, service in lowercase, age category (if age >= 65 then 'Senior', if age >= 18 then 'Adult', else 'Minor'), and name length. Only show patients whose name length is greater than 10 characters.
