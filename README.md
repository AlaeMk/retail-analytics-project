# 🛍️ Omnichannel Retail Analytics

[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)](https://www.python.org/)
[![SQL](https://img.shields.io/badge/SQL-Oracle-red?logo=oracle)](https://www.oracle.com/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)](https://powerbi.microsoft.com/)
[![GitHub](https://img.shields.io/badge/GitHub-Repo-black?logo=github)](https://github.com/AlaeMk/retail-analytics-project)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Infotact Internship Project** – End-to-end data analytics pipeline for omnichannel retail sales, from raw CSV to interactive dashboard.

---

## 📌 Project Overview

This project builds a complete data analytics solution for a multi‑channel retailer. It unifies **physical store** and **online** sales data, cleans and prepares the data, performs SQL aggregations and business metrics, and finally presents insights through an interactive **Power BI dashboard**.

**Key business questions answered:**
- Total revenue & average transaction value
- Sales by channel (Store, Website, MobileApp, etc.)
- Top‑selling product categories
- Monthly revenue trends
- Sales performance by city
- Customer spending patterns (running total, previous purchase growth, ranking)

---

## 📂 Repository Structure


---

## 🏆 Progress & Deliverables

| Week | Task | Status | Key Outputs |
|------|------|--------|--------------|
| **1** | Data Cleaning | ✅ Complete | Cleaned 6 CSV files; handled missing values, outliers, date formats; added time features |
| **2** | SQL Aggregations | ✅ Complete | 8 SQL queries (JOINs, GROUP BY, window functions); results include KPIs, city, monthly trend, top customers |
| **3** | Dashboard Creation | ✅ Complete | Interactive Power BI dashboard with monthly trend, category/city/day‑of‑week charts, and slicers for date, city, channel. Files: `dashboard/retail_dashboard.pbix` and screenshots. |
| **4** | Final Report & Insights | ⏳ Pending | PDF report with actionable business recommendations |

---

## 📊 Week 2 – SQL Results Snapshot

- **Total Revenue**: `$73,214,931.30`  
- **Total Transactions**: `641,843`  
- **Average Transaction Value**: `$114.07`  
- **Unique Customers**: `5,001`

### Top 5 Channels by Revenue:
1. **Store** – $30,231,970  
2. **Website** – $20,300,319  
3. **MobileApp** – $13,097,686  
4. **Amazon.ae** – $6,470,766  
5. **Noon** – $3,114,189

### Sales by City:
- 🏙️ **Dubai** – $41,044,846  
- 🏙️ **Abu Dhabi** – $20,493,650  
- 🏙️ **Sharjah** – $11,676,435

### Monthly Sales Pattern:
- Highest months: January (≈ $2M) across 2021–2025, February and July also strong.  
- Lowest months: March, September, October (≈ $700k–$800k).

### Top Products:
All top 10 products belong to **Electronics** (batteries, chargers, cables, mobile accessories).

---
## 📊 Week 3 – Power BI Dashboard

The interactive dashboard allows decision‑makers to filter by date range, city, and sales channel. Key visualisations include:

- **Monthly sales trend** (line chart)
- **Revenue by product category** (bar chart)
- **Sales by city** (bar chart)
- **Sales by day of week** (bar chart)
- **KPIs**: Total Revenue ($73.2M), Total Quantity (2M), Avg Order Value ($114), Unique Customers (5k)

All visuals respond to slicers, enabling drill‑down analysis for inventory and marketing planning.

📁 **Files:** [`dashboard/retail_dashboard.pbix`](https://github.com/AlaeMk/retail-analytics-project/tree/main/dashboard) 

---
## 🛠️ Tools & Technologies

- **Python** (Pandas, NumPy) – for data cleaning and preparation  
- **Oracle SQL Developer** – for writing and running analytical queries  
- **Power BI Desktop** – for interactive dashboard  
- **Git / GitHub** – version control and collaboration  

---

## 🚀 How to Reproduce This Project

1. **Clone the repository**  
   `git clone https://github.com/AlaeMk/retail-analytics-project.git`

2. **Data cleaning**  
   - Run the Jupyter notebook in `/notebooks/` to clean raw CSVs (if you have the original dataset) – or use the already cleaned files in `/data/cleaned/`.

3. **SQL analysis**  
   - Import the cleaned CSVs into Oracle Database (or any SQL engine).  
   - Execute the queries in `/sql/Omnichannel_Retail.sql` to reproduce the metrics.

4. **Dashboard**  
   - Open `retail_dashboard.pbix` in Power BI Desktop (once uploaded in Week 3).  
   - Refresh data connections if needed.

---

## 📝 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

## ✍️ Author

**Alae Mk** – Data Analytics Intern @ Infotact  
GitHub: [AlaeMk](https://github.com/AlaeMk)

---

*Last updated: May 2026 – Weeks 1, 2 & 3 completed.*
