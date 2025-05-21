# SQL Practice Scripts

This repository contains a collection of SQL queries to practice essential SQL concepts using a fictional dataset of `customers` and `orders`. The scripts are categorized and well-commented to demonstrate the use of various SQL clauses and features.

## 🗂️ Tables Used

- `customers`: Contains details about customers including `id`, `first_name`, `country`, and `score`.
- `orders`: Contains customer order data, including `order_date`.

---

## 📋 SQL Query Categories

### 🔍 Select Queries
- Retrieve all columns:
  SELECT * FROM customers;
  SELECT * FROM orders;
  
- Retrieve specific columns:
  SELECT first_name, country, score FROM customers;
  
📌 WHERE Clause
- Customers with a non-zero score:
  SELECT * FROM customers WHERE score != 0;

- Customers from Germany:
  SELECT first_name, country FROM customers WHERE country = 'Germany';

📊 ORDER BY Clause
- Sort customers by highest score:
  SELECT * FROM customers ORDER BY score DESC;
  
- Country and score (nested sorting):
  SELECT * FROM customers ORDER BY country ASC, score DESC;
  
📈 GROUP BY Clause
- Total score per country:
  SELECT country, SUM(score) AS total_score FROM customers GROUP BY country;

- Total score and customer count per country:
  SELECT country, SUM(score) AS total_score, COUNT(id) AS total_customers FROM customers GROUP BY country;

✅ HAVING Clause
-  Countries with an average score > 430:
  SELECT country, AVG(score) AS avg_score FROM customers GROUP BY country HAVING AVG(score) > 430;

-  Filtered by non-zero scores:
  SELECT country, AVG(score) AS avg_score 
  FROM customers 
  WHERE score != 0 
  GROUP BY country 
  HAVING AVG(score) > 430;

🧹 DISTINCT Clause
- List all unique countries:
  SELECT DISTINCT country FROM customers;

🎯 TOP Clause (SQL Server syntax)
- Top 3 customers by score:
  SELECT TOP 3 * FROM customers ORDER BY score DESC;

- Two most recent orders:
  SELECT TOP 2 * FROM orders ORDER BY order_date DESC;

🧪 Additional SQL Features
- Static values:
  SELECT 123 AS static_number;
  SELECT 'Hello' AS static_string;

- Assigning constant value to a query:
  SELECT id, first_name, 'New Customer' AS customer_type FROM customers;
