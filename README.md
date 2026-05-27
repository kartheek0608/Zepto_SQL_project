# 🛒 Zepto Inventory SQL Analysis Project

> A real-world SQL data analysis project on Zepto's product inventory dataset — covering data exploration, cleaning, and business insight queries using **PostgreSQL**.

---

## 📌 Project Overview

This project performs end-to-end SQL analysis on a Zepto inventory dataset sourced from Kaggle. The goal is to clean raw data, explore patterns, and extract meaningful business insights using structured SQL queries — simulating the kind of analysis done by a data analyst in a real e-commerce company.

---

## 🎯 Objectives

- Practice real-world SQL querying on e-commerce data
- Perform data cleaning and transformation in SQL
- Analyze product pricing, discounts, and stock availability
- Generate actionable business insights from raw inventory data

---

## 📂 Project Structure

```
Zepto_SQL_project/
│
├── Zepto_SQL_Analysis.sql    # All SQL queries (exploration, cleaning, insights)
├── zepto_v2.csv              # Raw Zepto inventory dataset (Kaggle)
└── README.md
```

---

## 🗂️ Dataset Description

**Source:** Kaggle — Zepto Inventory Dataset

Each row represents a unique **SKU (Stock Keeping Unit)**. The same product may appear multiple times across different package sizes, weights, or discounts — reflecting real catalog data.

| Column | Description |
|--------|-------------|
| `sku_id` | Unique identifier for each product SKU |
| `name` | Product name as shown on the app |
| `category` | Product category (Fruits, Snacks, Beverages, etc.) |
| `mrp` | Maximum Retail Price (converted from paise to ₹) |
| `discountPercent` | Discount % applied on MRP |
| `discountedSellingPrice` | Final price after discount (converted to ₹) |
| `availableQuantity` | Units available in inventory |
| `weightInGms` | Product weight in grams |
| `outOfStock` | Boolean — whether product is out of stock |
| `quantity` | Number of units per package |

---

## 🛠️ Tools & Technologies

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![pgAdmin](https://img.shields.io/badge/pgAdmin-336791?style=flat-square&logo=postgresql&logoColor=white)

---

## 🔧 Project Workflow

### 1. 🏗️ Table Creation
```sql
CREATE TABLE zepto (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150) NOT NULL,
    mrp NUMERIC(8,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGms INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
);
```

### 2. 🔍 Data Exploration
- Counted total records in the dataset
- Previewed sample rows to understand structure
- Checked for NULL values across all columns
- Listed distinct product categories
- Compared in-stock vs out-of-stock product counts
- Identified products with multiple SKUs

### 3. 🧹 Data Cleaning
- Removed rows where MRP or discounted price = 0
- Converted `mrp` and `discountedSellingPrice` from **paise → ₹** (divided by 100)

---

## 📊 Business Insight Queries

| # | Question | SQL Concept Used |
|---|----------|-----------------|
| Q1 | Top 10 best-value products by discount % | `ORDER BY`, `LIMIT` |
| Q2 | High-MRP products that are out of stock | `WHERE`, `FILTER` |
| Q3 | Estimated revenue per category | `SUM`, `GROUP BY` |
| Q4 | Premium products (MRP > ₹500) with low discount (<10%) | `WHERE` with multiple conditions |
| Q5 | Top 5 categories by average discount | `AVG`, `GROUP BY`, `LIMIT` |
| Q6 | Price per gram for products above 100g | Derived column, `ROUND` |
| Q7 | Weight category grouping (Low / Medium / Bulk) | `CASE WHEN` |
| Q8 | Total inventory weight per category | `SUM`, `GROUP BY` |

---

## 💡 Key Business Insights

- 🏷️ Several products offer **50%+ discounts** — ideal for promotional campaigns
- 📦 High-MRP out-of-stock products represent **lost revenue opportunities**
- 💰 Revenue is concentrated in a few top-performing categories
- ⚖️ Price-per-gram analysis helps identify the **best value products** for customers
- 🗃️ Bulk products dominate inventory weight but vary in availability

---

## ▶️ How to Run

1. Install **PostgreSQL** and open **pgAdmin** (or any SQL client)
2. Create a new database
3. Import `zepto_v2.csv` using pgAdmin's import feature into the `zepto` table
4. Open `Zepto_SQL_Analysis.sql` and run queries step by step

```bash
# Or via psql CLI
psql -U postgres -d your_database
\i Zepto_SQL_Analysis.sql
```

---

## 📈 What I Learned

- Writing optimized, real-world SQL queries
- Handling and cleaning raw e-commerce datasets
- Using `CASE WHEN`, `GROUP BY`, `HAVING`, derived columns
- Translating business questions into SQL logic
- Generating insights that drive data-driven decisions

---

## 👨‍💻 Author

**Ryalampadu Kartheek**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kartheek-ryalampadu)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:kartheekryalampadu@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/kartheek-r)


