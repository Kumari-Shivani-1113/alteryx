# 🔄 Customer Sales Report — Alteryx Designer

An automated ETL workflow built in Alteryx Designer that processes multi-format data sources, performs data cleaning and joining, and produces a ranked **Top 10 High-Value Customer Sales Report**.

---

## 📌 Project Overview

| | |
|---|---|
| **Tool** | Alteryx Designer 2025.1 |
| **Input Sources** | Customers.csv, Transactions.xml, OnlineRetail_UCI.xlsx |
| **Output** | Customer_sales_report.xlsx (Top 10 customers by sales) |
| **Goal** | Identify top non-responding high-value customers for re-engagement |

---

## 🔄 Workflow Pipeline

```
Customers.csv ──► Select ──► Filter ──► Cleanse ──────────────►
                 (rename &   (Responder                         Join ──► Sort ──► Sample ──► Output
                 data types)  = "No" only)                      ↑       (Sales,   (Top 10)   (.xlsx)
                                                                 │        Desc)
Transactions.xml ──► Select ─────────────────────────────────────┘
                    (data types)                    │
                                                 Test Tool
                                          (flag unmatched records)
```

---

## 🛠️ Tools Used in Workflow

| Tool | Purpose |
|---|---|
| **Input (x2)** | Read Customers.csv and Transactions.xml |
| **Select (x2)** | Rename columns, convert data types (CustomerID → Int16, Sales → Double) |
| **Filter** | Keep only customers where `Responder = "No"` |
| **Cleanse Macro** | Trim whitespace, fix title case on First Name & Last Name |
| **Join** | Match customers to transactions on Customer ID key |
| **Test** | Flag transactions with no matching customer (data quality check) |
| **Sort** | Order results by Total Sales — Descending |
| **Sample** | Extract Top 10 rows only |
| **Output** | Export final report to Excel |

---

## 📂 Data Sources

### 1. Customers.csv
Customer demographic data from Alteryx sample dataset.

| Field | Description |
|---|---|
| CustomerID | Unique customer identifier |
| Store Number | Store associated with customer |
| Customer Segment | Customer category |
| Responder | Whether customer responded to marketing (Yes/No) |
| First Name, Last Name | Customer name |
| Address, City, State, Zip | Location data |
| Lat, Lon | Geographic coordinates |

### 2. Transactions.xml
Sales transaction records from Alteryx sample dataset.

| Field | Description |
|---|---|
| Transaction | Transaction ID |
| Customer_ID | Links to CustomerID in Customers.csv |
| Product_Name | Name of product purchased |
| Sales | Sale amount ($) |
| Order_ID | Order reference number |

### 3. OnlineRetail_UCI.xlsx
UCI Machine Learning Repository — Online Retail Dataset (2010–2011).

| Field | Description |
|---|---|
| InvoiceNo | Invoice number |
| StockCode | Product code |
| Description | Product description |
| Quantity | Units purchased |
| InvoiceDate | Date & time of purchase |
| UnitPrice | Price per unit |
| CustomerID | Customer identifier |
| Country | Country of customer |

> **541,910 rows** of transactional data from a UK-based online retailer selling across multiple countries.

---

## 📊 Key Findings

- Filtered out marketing **responders** to focus on **non-responding high-value customers**
- Joined customer profiles with transaction history to calculate **total sales per customer**
- Identified **Top 10 customers by total sales** — prime targets for re-engagement campaigns
- Data quality check revealed any **unmatched transactions** (orphaned records with no customer profile)

---

## 📸 Workflow Preview

![Alteryx Workflow](screenshots/workflow.png)

---

## 📁 Files in This Repo

| File | Description |
|---|---|
| `Customer_sales_report.yxmd` | Alteryx Designer workflow file |
| `data/OnlineRetail_UCI.xlsx` | UCI Online Retail dataset (541,910 rows) |
| `screenshots/` | Workflow and output screenshots |

---

## 🛠️ Skills Demonstrated

- **Alteryx Designer** — drag-and-drop ETL workflow design
- **ETL (Extract, Transform, Load)** — multi-format data ingestion and processing
- **Data Blending** — joining CSV and XML sources on a common key
- **Data Cleansing** — type conversion, whitespace trimming, title case standardization
- **Data Quality Testing** — flagging unmatched/orphaned records
- **Workflow Automation** — end-to-end automated pipeline from raw data to Excel report

---

## 💼 Resume Description

> Built an automated ETL workflow in Alteryx Designer processing multi-format data sources (CSV and XML). Applied data cleansing, type conversion, filtering, and joining to identify the Top 10 high-value non-responding customers by total sales. Separately analyzed a 541,910-row UCI Online Retail dataset covering international retail transactions from 2010–2011.

---

*Built by Kumari Shivani Fnu*
