# 📊 SQL DISTINCT Keyword | Removing Duplicate Results

## 🎯 Overview

The SQL `DISTINCT` keyword eliminates duplicate rows from query results and returns unique values or combinations.

It is commonly used in data exploration, customer analysis, retail reporting, and business intelligence.

**Objective:** Understand DISTINCT, apply it to single and multiple columns, combine it with WHERE and ORDER BY, and compare it with UNIQUE and GROUP BY.

---

## 1️⃣ What is DISTINCT?

`DISTINCT` removes duplicate rows from a SELECT query's result set.

### Basic Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

### Sample Dataset: sales_data

| Customer | City |
|---|---|
| Amit | Hyderabad |
| Ravi | Mumbai |
| Amit | Hyderabad |
| Neha | Pune |
| Ravi | Mumbai |

### SQL Query

```sql
SELECT DISTINCT customer, city
FROM sales_data;
```

### Output

| Customer | City |
|---|---|
| Amit | Hyderabad |
| Ravi | Mumbai |
| Neha | Pune |

**Explanation:** Repeated customer-city combinations appear only once.

**Important:** DISTINCT removes duplicates from the query result, not from the original table.

---

## 2️⃣ DISTINCT on a Single Column

Retrieve unique cities from customer records.

```sql
SELECT DISTINCT city
FROM customers;
```

### Sample Output

| City |
|---|
| Hyderabad |
| Mumbai |
| Pune |

**Business Use Case:** Identify cities represented in a customer database.

---

## 3️⃣ DISTINCT on Multiple Columns

DISTINCT evaluates the combination of all selected columns.

```sql
SELECT DISTINCT city, category
FROM stores;
```

### Sample Output

| City | Category |
|---|---|
| Hyderabad | Electronics |
| Hyderabad | Grocery |
| Mumbai | Electronics |

**Explanation:** A city can appear multiple times if its associated category differs.

DISTINCT does not enforce uniqueness independently on each selected column.

---

## 4️⃣ DISTINCT with WHERE

WHERE filters records before DISTINCT removes duplicate results.

### Example: Products from High-Value Transactions

```sql
SELECT DISTINCT product
FROM sales
WHERE sales > 10000;
```

**Business Use Case:** Identify products appearing in transactions exceeding ₹10,000.

### Processing Logic

1. FROM identifies the source table.
2. WHERE filters individual records.
3. SELECT identifies the output.
4. DISTINCT eliminates duplicate result rows.

---

## 5️⃣ DISTINCT with ORDER BY

ORDER BY sorts the final results.

```sql
SELECT DISTINCT payment_method
FROM transactions
ORDER BY payment_method;
```

### Sample Output

| Payment Method |
|---|
| Card |
| Cash |
| UPI |

**Business Use Case:** Retrieve a sorted list of available payment methods.

---

## 6️⃣ DISTINCT vs UNIQUE vs GROUP BY

| Feature | DISTINCT | UNIQUE | GROUP BY |
|---|---|---|---|
| Purpose | Removes duplicate result rows | Enforces uniqueness | Groups records |
| Usage | SELECT queries | Database constraints | SELECT queries |
| Main Benefit | Unique query results | Data integrity | Grouped analysis |

### DISTINCT Example

```sql
SELECT DISTINCT category
FROM products;
```

Returns unique product categories.

### UNIQUE Constraint Example

```sql
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE
);
```

Prevents duplicate non-NULL email values from being stored.

*NULL handling depends on the database system.*

### GROUP BY Example

```sql
SELECT
    category,
    COUNT(*) AS product_count
FROM products
GROUP BY category;
```

Returns product counts for each category.

**Key Difference:** DISTINCT focuses on unique results, while GROUP BY is commonly used for aggregation.

---

## 7️⃣ COUNT(DISTINCT)

COUNT(DISTINCT) calculates the number of unique non-NULL values.

### Example: Unique Customers

```sql
SELECT
    COUNT(DISTINCT customer_id)
        AS unique_customers
FROM transactions;
```

**Business Use Case:** Measure the number of distinct customers who made transactions.

### COUNT vs COUNT(DISTINCT)

```sql
SELECT
    COUNT(customer_id) AS customer_records,
    COUNT(DISTINCT customer_id) AS unique_customers
FROM transactions;
```

- COUNT(customer_id) counts non-NULL customer IDs.
- COUNT(DISTINCT customer_id) counts unique non-NULL customer IDs.

---

## 8️⃣ Real-World Business Applications

### 👥 Customer Analytics

Identify unique customers.

```sql
SELECT DISTINCT customer_id
FROM transactions;
```

### 📦 Retail Analytics

Identify distinct products sold.

```sql
SELECT DISTINCT product
FROM sales;
```

### 💳 Payment Analytics

Retrieve available payment methods.

```sql
SELECT DISTINCT payment_method
FROM transactions;
```

### 🏬 Store Analytics

Identify unique store categories.

```sql
SELECT DISTINCT category
FROM stores;
```

### 📊 Business Reporting

```sql
SELECT DISTINCT region, category
FROM sales;
```

Identify unique region-category combinations for analysis.

---

## 9️⃣ Performance Considerations

DISTINCT may require additional processing when handling large datasets.

### Best Practices

✅ Select only necessary columns.

✅ Apply WHERE filters when appropriate.

✅ Avoid DISTINCT when uniqueness is already guaranteed.

✅ Review execution plans for expensive queries.

✅ Consider suitable indexes for frequently queried columns.

✅ Do not use DISTINCT to hide incorrect joins or underlying data-quality problems.

**Note:** DISTINCT does not always slow queries down. Performance depends on indexes, dataset size, selected columns, and query execution plans.

---

## 🔟 SQL Interview Questions

**Q1. What is DISTINCT?**

DISTINCT removes duplicate rows from a query result.

**Q2. Can DISTINCT work on multiple columns?**

Yes. It returns unique combinations of selected column values.

**Q3. DISTINCT vs UNIQUE?**

DISTINCT removes duplicate result rows; UNIQUE enforces a database constraint.

**Q4. DISTINCT vs GROUP BY?**

DISTINCT retrieves unique results; GROUP BY groups rows, commonly for aggregate calculations.

**Q5. Does DISTINCT modify original data?**

No. It only affects the query output.

**Q6. How does DISTINCT handle NULL?**

For duplicate elimination, multiple NULL values in the same selected position are treated as duplicates.

**Q7. What is COUNT(DISTINCT)?**

It counts unique non-NULL values.

---

## 🎯 Key Takeaways

✅ DISTINCT retrieves unique result rows.

✅ It works with single or multiple columns.

✅ WHERE can filter records before DISTINCT.

✅ ORDER BY sorts DISTINCT results.

✅ UNIQUE enforces data integrity.

✅ GROUP BY supports grouped analysis.

✅ COUNT(DISTINCT) counts unique non-NULL values.

✅ DISTINCT should be used thoughtfully on large datasets.

---

## 💡 Final Thoughts

**SQL DISTINCT helps analysts eliminate repetitive query results and focus on meaningful unique values.**

Understanding DISTINCT, UNIQUE, and GROUP BY supports accurate data exploration, business reporting, and better analytical decisions.

### 🏷️ Topics

`SQL` `DISTINCT` `COUNT DISTINCT` `UNIQUE` `GROUP BY` `WHERE` `ORDER BY` `Data Analytics` `Business Analytics` `MySQL` `Data Cleaning`
