# sql-ecommerce-analysis
End-to-end e-commerce sales data analysis using SQL Server — includes SELECT, WHERE, GROUP BY, aggregate functions, subqueries, indexes, and views.

# 🛒 E-Commerce Sales Data Analysis (SQL Project)

## 📘 Overview
This project focuses on performing **data analysis** on an e-commerce sales dataset using **Microsoft SQL Server**.  
Various SQL operations — including aggregate functions, filtering, indexing, subqueries, and views — were implemented to extract meaningful business insights.

---

## 🧩 Database Used
**Database name:** `e_commerce`  
**Table used:** `sales_data`

| Column Name | Description |
|--------------|-------------|
| Order Date | Date of the order |
| Order ID | Unique identifier for each order |
| Product | Product name |
| Categories | Product category |
| Quantity Ordered | Number of items ordered |
| Price Each | Price per item |
| Cost Price | Cost per item |
| Turnover | Total sales revenue |
| Margin | Profit margin |
| Purchase Address | Shipping address |

---

## ⚙️ SQL Operations and Queries

### 1. **Basic SELECT Statement**
```sql
SELECT * 
FROM sales_data;
```
Retrieves all columns from the `sales_data` table for an overview of the dataset.

---

### 2. **Aggregate Functions**
```sql
SELECT 
    SUM(turnover) AS Total_Turnover,
    AVG(margin) AS Average_Margin
FROM sales_data;
```
Calculates total turnover and average margin across all sales records.

---

### 3. **Creating Indexes**
```sql
CREATE INDEX idx_orderdate ON sales_data([Order Date]);
CREATE INDEX idx_category ON sales_data(Categories);
CREATE INDEX idx_product ON sales_data(Product);
CREATE INDEX idx_turnover ON sales_data(turnover);
```
Indexes improve query performance for commonly searched columns such as order date, category, product, and turnover.

---

### 4. **Creating a View**
```sql
CREATE VIEW vw_CategorySales AS
SELECT 
    Categories, 
    SUM(turnover) AS TotalSales, 
    SUM(margin) AS TotalMargin
FROM sales_data
GROUP BY Categories;
```
A reusable **view** that summarizes total sales and total margin per category.

---

### 5. **Using the View**
```sql
SELECT * 
FROM vw_CategorySales;
```
Displays pre-aggregated sales data by category.

---

### 6. **GROUP BY with ORDER BY**
```sql
SELECT 
    Categories, 
    SUM(turnover) AS TotalSales
FROM sales_data
GROUP BY Categories
ORDER BY TotalSales DESC;
```
Groups sales by category and orders them by highest total sales — identifying top-performing categories.

---

### 7. **Filtering with WHERE Clause**
```sql
SELECT 
    [Order Date], 
    Product, 
    turnover
FROM sales_data
WHERE turnover > 500;
```
Filters records to show only transactions where turnover exceeds 500.

---

### 8. **Subquery**
```sql
SELECT 
    Categories, 
    Product, 
    turnover
FROM sales_data
WHERE turnover IN (
    SELECT MAX(turnover)
    FROM sales_data
    GROUP BY Categories
);
```
Identifies the **highest-turnover product** in each category.

---

### 9. **ORDER BY Example**
```sql
SELECT 
    Product, 
    margin
FROM sales_data
ORDER BY margin DESC;
```
Displays products sorted by highest profit margin.

---

## 📊 Results Summary
| Query Type | Outcome |
|-------------|----------|
| Aggregates | Calculated total turnover and average margin |
| Indexes | Improved query performance |
| View | Simplified category-level sales summaries |
| Grouping | Ranked sales categories by performance |
| Filtering | Isolated high-revenue transactions |
| Subquery | Found top-selling product per category |
| Ordering | Displayed top-margin products |

---

## 🧠 Key Insights
- **Top Category:** Sports generated the highest total sales.  
- **High-Margin Products:** MacBook Pro Laptops showed consistently high margins.  
- **Efficient Querying:** Index creation reduced query execution time.  
- **Reusable Views:** Simplified analysis of sales and margin by category.

---

## 🛠 Tools & Environment
- **SQL Server Management Studio (SSMS)**  
- **Microsoft SQL Server 16.0 RTM**  
- **Dataset:** `sales_data` (approx. 227,926 rows)

---

## 📸 Screenshots
Included in the repository:
- `Agg functions.jpg` → Aggregate functions query  
- `created indexes.jpg` → Index creation  
- `created view.jpg` → View creation  
- `group by.jpg` → Group by category  
- `order by.jpg` → Ordered sales results  
- `select statement.jpg` → Dataset preview  
- `subquery.jpg` → Highest turnover subquery  
- `views.jpg` → View execution  
- `where.jpg` → Filtered turnover query  

---

## 🧾 Author
**Name:** *Vinay B*  
**Date:** *October 2025*

