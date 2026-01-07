# Market Basket Analysis: Identifying Products Purchased Together

## Overview

This project performs a **market basket analysis** to identify which products are most frequently purchased together. Using a combination of **SQL** and **pandas**, the analysis mirrors a realistic analytics workflow: raw transactional data is cleaned, queried in a relational database, analyzed in Python, and summarized with visualizations and exportable results.

The goal of the project is not only to surface common product pairings, but to translate those findings into **actionable business insights** that could inform bundling strategies, cross-selling, and product placement decisions.

---

## Business Question

> *Which products are most likely to be purchased together, and how can this information be used to support business decisions?*

---

## Dataset

* Transaction-level retail data
* Each row represents a product purchased on a specific invoice
* Key fields include:

  * **InvoiceNo**: Unique transaction identifier
  * **Description**: Product name
  * **Quantity**: Number of units purchased
  * **UnitPrice**: Price per unit
  * **CustomerID**: Customer identifier

*(Exact dataset details are documented within the notebook.)*

---

## Tools & Technologies

* **Python**: pandas, matplotlib
* **SQL**: SQLite (via `sqlite3`)
* **Jupyter Notebook**

---

## Methodology

### 1. Data Cleaning & Preparation

* Removed missing or invalid product descriptions
* Filtered out cancelled or non-positive quantity transactions
* Ensured consistency between SQL and pandas data representations

### 2. SQL-Based Analysis

* Loaded cleaned data into a SQLite database
* Used SQL to:

  * Aggregate transactions at the invoice level
  * Identify frequently purchased product combinations
  * Summarize revenue and customer behavior

### 3. Market Basket Analysis

* Each invoice is treated as a single transaction
* Products are represented as **binary indicators** (present or not present per transaction)
* Product pairs are evaluated using **support**:

[ Support(A, B) = \frac{\text{Transactions containing both A and B}}{\text{Total transactions}} ]

Support was chosen to highlight commonly co-occurring products in an exploratory context.

### 4. Visualization & Interpretation

* Bar charts highlight the most frequent product pairings
* A heatmap visualizes co-occurrence intensity across popular products

---

## Key Findings

* A small subset of products consistently appears in the most frequent pairings
* Many co-purchased items are low-cost, high-frequency goods
* Certain products act as "anchors," appearing alongside a wide range of other items

---

## Business Implications

* **Bundling Opportunities**: Frequently co-purchased products are strong candidates for bundle discounts
* **Cross-Selling**: Pairings can be used to power recommendation systems ("Customers also bought")
* **Product Placement**: High co-occurrence items may benefit from closer physical or digital placement

---

## Limitations & Next Steps

* Analysis is based solely on historical transaction data
* Customer segmentation and seasonality were not explored
* Future improvements could include:

  * Confidence and lift metrics
  * Time-based purchasing patterns
  * Segment-specific market basket analysis

---

## Files

* `Analysis.ipynb`: Full analysis notebook
* `co_purchased_products.csv`: Exported product pair results
