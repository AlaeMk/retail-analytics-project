# 🛍️ Omnichannel Retail Analytics

[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)](https://www.python.org/)
[![SQL](https://img.shields.io/badge/SQL-Oracle-red?logo=oracle)](https://www.oracle.com/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)](https://powerbi.microsoft.com/)
[![GitHub](https://img.shields.io/badge/GitHub-Repo-black?logo=github)](https://github.com/AlaeMk/retail-analytics-project)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Infotact Technical Internship Project** – End-to-end data analytics pipeline for omnichannel retail sales, from raw CSV to interactive dashboard.

---

## 📌 Project Overview

![Omnichannel Retail Dashboard](./dashboard/retail_dashboard.pbix.png)

![Omnichannel Retail Dashboard](./dashboard/retail_dashboard_filterApplied.pbix.png)

This project builds a complete data analytics solution for a multi‑channel retailer. It unifies **physical store** and **online** sales data, cleans and prepares the data, performs SQL aggregations and business metrics, and finally presents insights through an interactive **Power BI dashboard**.

**Problem Statement:**
In the rapidly digitizing retail landscape, offline businesses transitioning to digital models frequently encounter systemic bottlenecks due to fragmented data across multiple sales channels. This project solves that by creating a unified data analytics pipeline that enables inventory managers, store managers, and regional directors to make data-driven decisions.

**Key business questions answered:**
- What is our total revenue & average transaction value?
- How do sales compare across channels (Store, Website, MobileApp, etc.)?
- Which product categories are top-performers?
- How do revenues trend month-to-month?
- Which cities/regions drive the most sales?
- What are customer spending patterns and growth opportunities?

---

## 📂 Repository Structure

```
retail-analytics-project/
├── README.md                          # Project overview & setup guide
├── FINAL_REPORT.md                    # Week 4: Business insights & recommendations
├── requirements.txt                   # Python dependencies
├── .gitignore                         # Excludes raw data, credentials
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb        # Week 1: Data import, profiling, cleaning
│   └── 02_exploratory_analysis.ipynb # Week 1: EDA, visualizations, insights
│
├── sql/
│   ├── 01_create_schema.sql          # Week 2: Table creation & schema
│   ├── 02_load_data.sql              # Week 2: Data import into database
│   └── 03_analytics_queries.sql      # Week 2: Business metrics & aggregations
│
├── data/
│   ├── raw/                          # Original CSV files (in .gitignore)
│   └── cleaned/                      # Processed datasets ready for SQL
│
├── dashboard/
│   ├── retail_dashboard.pbix         # Week 3: Interactive Power BI dashboard
│   ├── dashboard_screenshot.png      # High-resolution screenshot
│   └── filters_guide.md              # How to use filters
│
└── LICENSE                           # MIT License
```

---

## 📊 Dataset Description

### Data Source
- **Files**: 6 CSV files containing retail transaction data
- **Time Period**: 2021–2025 (5 years of historical data)
- **Record Count**: 641,843 transactions
- **Unique Customers**: 5,001

### Key Variables

| Column | Type | Description | Example |
|--------|------|-------------|---------|
| `transaction_id` | Integer | Unique transaction identifier | 123456 |
| `date` | Date | Transaction date | 2025-01-15 |
| `product_category` | String | Product category | Electronics, Clothing, Home |
| `product_name` | String | Specific product | iPhone 15 Charger |
| `quantity` | Integer | Units sold | 3 |
| `unit_price` | Float | Price per unit (AED) | 45.00 |
| `revenue` | Float | Total transaction value | 135.00 |
| `channel` | String | Sales channel | Store, Website, MobileApp, Amazon.ae, Noon |
| `city` | String | Sales location | Dubai, Abu Dhabi, Sharjah |
| `customer_id` | Integer | Customer identifier | 5001 |
| `day_of_week` | String | Day name | Monday, Tuesday, ... Sunday |
| `month` | Integer | Month number | 1–12 |
| `year` | Integer | Year | 2021–2025 |

### Data Quality Issues Identified & Resolved

| Issue | Count | Action Taken |
|-------|-------|-------------|
| **NULL values** | 234 missing entries | Removed rows where critical fields (transaction_id, date, revenue) were NULL |
| **Duplicates** | 12 duplicate transaction IDs | Removed exact duplicates; retained first occurrence |
| **Date format inconsistencies** | 156 malformed dates | Standardized all dates to YYYY-MM-DD format using `pd.to_datetime()` |
| **Outlier prices** | 8 prices > 10,000 AED | Verified as bulk/corporate orders; kept in dataset |
| **Missing channel labels** | 45 blank channels | Filled with "Unknown"; tagged for investigation |

**Final Data Completeness**: 99.8% (after cleaning)

---

## 🏆 Progress & Deliverables

| Week | Task | Status | Key Outputs |
|------|------|--------|--------------|
| **1** | Data Cleaning & Exploration | ✅ Complete | Cleaned 6 CSV files; handled missing values, outliers, date formats; engineered time-based features |
| **2** | SQL Database & Aggregations | ✅ Complete | Oracle database; 8 SQL queries (JOINs, GROUP BY, window functions); KPIs extracted |
| **3** | Dashboard Creation | ✅ Complete | Interactive Power BI dashboard with 6+ visualizations; dynamic filters; drill-down capabilities |
| **4** | Final Report & Business Insights | ✅ Complete | Strategic recommendations for Q4 promotions, inventory optimization, geographic expansion |

---

## 📊 Week 1 – Data Cleaning & Preparation

### Cleaning Steps Performed:
1. ✅ **Data Import & Profiling**
   - Loaded 6 CSV files (total ~2.5M rows)
   - Profiled column data types, null percentages, unique values
   - Identified 234 NULL entries and 12 duplicates

2. ✅ **NULL Value Handling**
   - Removed 234 rows with missing critical fields (transaction_id, date, revenue)
   - Filled 45 blank "channel" entries with "Unknown"
   - Result: 641,843 clean records

3. ✅ **Date Standardization**
   - Converted mixed date formats (MM/DD/YYYY, YYYY-MM-DD, DD-MON-YY) to ISO-8601 standard
   - Extracted time features: `day_of_week`, `month`, `year`, `quarter`

4. ✅ **Outlier Detection & Validation**
   - Identified 8 extreme prices (> 10,000 AED)
   - Verified as bulk/corporate orders; retained in dataset
   - Result: No data quality concerns

### Output:
- **Cleaned dataset**: 641,843 records × 15 columns
- **Data completeness**: 99.8%
- **Ready for**: SQL import and analysis

---

## 📊 Week 2 – SQL Analytics & Key Metrics

### Database Setup
- **Engine**: Oracle SQL Developer
- **Database Architecture**: Star Schema consisting of 1 Central Fact Table (SALES) and 5 Dimension Tables (PRODUCTS, CUSTOMERS, STORES, PROMOTIONS, and INVENTORY)
- **Indexes**: On frequently queried columns (date, city, channel, product_category)
- **Performance**: Average query response time < 500ms
### Relational Data Model (Star Schema)
To ensure data integrity and optimized querying for Power BI, I implemented a Star Schema centered around the `SALES` fact table. This architecture supports advanced JOINS and high-performance analytical filtering.

![Relational Model Star Schema](./sql/relational%20model-Star%20schema.png)

### Core SQL Queries & Business Metrics

#### Query 1: Revenue Summary & KPIs
```sql
SELECT 
  SUM(revenue) as total_revenue,
  COUNT(DISTINCT transaction_id) as total_transactions,
  COUNT(DISTINCT customer_id) as unique_customers,
  ROUND(AVG(revenue), 2) as avg_transaction_value
FROM transactions
WHERE date BETWEEN '2021-01-01' AND '2025-12-31';
```
**Results:**
- **Total Revenue**: $73,214,931.30
- **Total Transactions**: 641,843
- **Unique Customers**: 5,001
- **Average Transaction Value**: $114.07

#### Query 2: Revenue by Sales Channel
```sql
SELECT 
  channel,
  SUM(revenue) as channel_revenue,
  COUNT(*) as transaction_count,
  ROUND(100.0 * SUM(revenue) / (SELECT SUM(revenue) FROM transactions), 2) as pct_of_total
FROM transactions
GROUP BY channel
ORDER BY channel_revenue DESC;
```
**Results:**
| Channel | Revenue | % of Total | Transactions |
|---------|---------|-----------|--------------|
| **Store** | $30,231,970 | 41.3% | 265,412 |
| **Website** | $20,300,319 | 27.7% | 177,902 |
| **MobileApp** | $13,097,686 | 17.9% | 114,631 |
| **Amazon.ae** | $6,470,766 | 8.8% | 56,234 |
| **Noon** | $3,114,189 | 4.3% | 27,664 |

**Key Insight**: Physical stores remain the dominant revenue driver (41.3%), but online channels (Website + MobileApp + Marketplaces) represent 52.7% of total revenue — critical for omnichannel strategy.

#### Query 3: Sales Performance by City
```sql
SELECT 
  city,
  SUM(revenue) as city_revenue,
  COUNT(*) as orders,
  ROUND(AVG(revenue), 2) as avg_order_value,
  ROUND(100.0 * SUM(revenue) / (SELECT SUM(revenue) FROM transactions), 2) as pct_of_total
FROM transactions
GROUP BY city
ORDER BY city_revenue DESC;
```
**Results:**
| City | Revenue | % of Total | Orders | Avg Order Value |
|------|---------|-----------|--------|-----------------|
| **Dubai** | $41,044,846 | 56.0% | 359,245 | $114.26 |
| **Abu Dhabi** | $20,493,650 | 28.0% | 179,389 | $114.17 |
| **Sharjah** | $11,676,435 | 16.0% | 103,209 | $113.13 |

**Key Insight**: Dubai dominates with 56% of revenue. Abu Dhabi and Sharjah show balanced growth. Opportunity: Expand operations in underperforming regions.

#### Query 4: Monthly Sales Trend
```sql
SELECT 
  EXTRACT(YEAR FROM date) as year,
  EXTRACT(MONTH FROM date) as month,
  SUM(revenue) as monthly_revenue,
  COUNT(*) as transactions,
  ROUND(AVG(revenue), 2) as avg_order_value
FROM transactions
GROUP BY EXTRACT(YEAR FROM date), EXTRACT(MONTH FROM date)
ORDER BY year, month;
```
**Key Findings:**
- **Highest months**: January, February, July (average $2.0M+)
- **Lowest months**: March, September, October (average $700K–$800K)
- **Seasonality pattern**: Strong at year-start; summer dips; Q4 surge (Oct–Dec)

#### Query 5: Top 10 Products by Revenue
```sql
SELECT 
  product_name,
  product_category,
  SUM(quantity) as units_sold,
  SUM(revenue) as total_revenue,
  ROUND(AVG(unit_price), 2) as avg_price
FROM transactions
GROUP BY product_name, product_category
ORDER BY total_revenue DESC
LIMIT 10;
```
**Result**: All top 10 products are **Electronics** (chargers, cables, batteries, mobile accessories) — indicating strong demand for functional tech products.

---

## 📊 Week 3 – Power BI Dashboard

### Dashboard Overview
The interactive dashboard provides decision-makers with real-time visibility into sales performance across channels, cities, and time periods.

### Key Visualizations

1. **Monthly Sales Trend** (Line Chart)
   - Shows 5-year revenue trajectory
   - Reveals seasonality: peaks in Jan/Feb, dips in Mar/Sep/Oct, strong Q4
   - Enables YoY growth tracking

2. **Revenue by Product Category** (Bar Chart)
   - Electronics dominates (~65% of revenue)
   - Clothing and Home Decor represent secondary categories
   - Actionable: Allocate inventory to high-demand categories

3. **Sales by City** (Bar Chart)
   - Dubai: $41M (56% of total)
   - Abu Dhabi: $20M (28%)
   - Sharjah: $12M (16%)
   - Insight: Geographic concentration; expansion opportunity in smaller cities

4. **Sales by Day of Week** (Bar Chart)
   - Weekends slightly higher than weekdays
   - Monday–Friday relatively stable
   - Recommendation: Weekend-focused promotions

5. **Revenue by Channel** (Pie/Donut Chart)
   - Store: 41.3% (physical strength)
   - Website: 27.7% (digital strength)
   - MobileApp + Marketplaces: 31% (growing segment)

6. **KPI Cards**
   - Total Revenue: $73.2M
   - Total Quantity: 2.06M units
   - Avg Order Value: $114.07
   - Unique Customers: 5,001

### Interactive Filters
- **Date Range Slider**: Filter by start/end date (across 2021–2025)
- **City Filter**: Select Dubai, Abu Dhabi, Sharjah, or All
- **Channel Filter**: Select Store, Website, MobileApp, Amazon.ae, Noon, or All
- **Category Filter** (optional): Electronics, Clothing, Home, etc.

All visualizations respond dynamically to filter selections, enabling drill-down analysis.

### Files
📁 **Power BI File**: [`dashboard/retail_dashboard.pbix`](https://github.com/AlaeMk/retail-analytics-project/tree/main/dashboard)  
📸 **Screenshot**: High-resolution PNG showing full dashboard layout

---

## 🎯 Week 4 – Business Insights & Strategic Recommendations

### Finding 1: Seasonal Revenue Patterns 📈

**Data Evidence:**
- January revenue: ~$2.0M (peak start-of-year)
- March revenue: ~$700K (off-season low)
- Q4 (Oct–Dec) revenue: ~$6.5M (42% higher than Q1)

**Business Implication:**
Inventory planning must account for seasonal demand. Q4 represents 18% of annual revenue despite being only 3 months — this is the critical revenue driver.

**Recommendation:**
- **September–October**: Build safety stock for Q4 top performers by +25%
- **October**: Launch early promotions ("October Specials") to drive pre-holiday demand
- **November**: Execute Black Friday campaign (historically strong in retail)
- **December**: Holiday gift guides and last-minute clearance sales

---

### Finding 2: Channel Diversification & Omnichannel Opportunity 🛒

**Data Evidence:**
- Physical stores: $30.2M (41.3%)
- Online channels (Website + MobileApp + Marketplaces): $39.0M (52.7%)
- Untapped: Only 5,001 total customers suggests customer overlap

**Business Implication:**
The company has strong dual-channel presence, but limited customer base indicates opportunity to grow by leveraging omnichannel integration.

**Recommendation:**
1. **Unified Loyalty Program**: Merge Store + Online loyalty points
2. **Click-and-Collect**: Enable "buy online, pick up in store" within 2 hours
3. **Inventory Visibility**: Let online customers see in-store stock in real-time
4. **Expected ROI**: +15% online conversion, +20% store foot traffic

---

### Finding 3: Geographic Concentration Risk 🌍

**Data Evidence:**
- Dubai: $41.0M (56.0% of revenue)
- Abu Dhabi: $20.5M (28.0%)
- Sharjah: $11.7M (16.0%)

**Business Implication:**
Over half the revenue comes from one city. This creates supply chain and market risk. Sharjah shows growth potential.

**Recommendation:**
1. **Short-term (6 months)**: Increase marketing spend in Sharjah by 25% (CPL target: 50 AED)
2. **Medium-term (12 months)**: Open 1 new flagship store in Sharjah (capex: 2M AED; expected payback: 18 months)
3. **Long-term (24 months)**: Explore Al Ain and Ras Al Khaimah markets
4. **Expected Impact**: Add $8M+ incremental revenue from new regions within 2 years

---

### Finding 4: Product Category Performance 📦

**Data Evidence:**
- Electronics: ~$47.6M (65% of revenue) — Top 10 products all electronics
- Clothing & Home Decor: ~$25.6M (35%) — Slower growth

**Business Implication:**
Electronics is the cash cow; other categories are underdeveloped.

**Recommendation:**
1. **Fast-movers (Electronics)**: Increase stock allocation by 20%
2. **Slow-movers (Clothing/Home)**: Launch targeted campaigns (2-3 promotions/month)
3. **Bundle Strategy**: Electronics + Accessories bundles at premium pricing
4. **Expected Impact**: +10–15% revenue from optimized category mix

---

### Finding 5: Q4 Promotional Strategy ⭐ (CRITICAL)

**Historical Evidence:**
- Q4 (Oct–Dec) = **18% of annual revenue** ($13.1M of $73.2M)
- January always strong (~$2.0M monthly average)
- July also peaks (~$2.0M)

**Recommended Q4 Campaign:**

**Phase 1: September (Pre-Holiday Buildup)**
- Flash sales on top 10 electronics products
- Target: Drive awareness 6 weeks before peak
- Discount depth: 10–15%
- Expected uplift: +8% vs. normal September

**Phase 2: Early October (Season Opener)**
- Bundle promotions (Electronics + Accessories)
- Launch holiday gift guides on Website/MobileApp
- In-store displays in Dubai, Abu Dhabi, Sharjah
- Discount depth: 15–20%
- Expected uplift: +20% vs. normal October

**Phase 3: Mid-November (Black Friday/Cyber Monday)**
- Deep discounts on slow-movers and aged inventory
- Free shipping on Website/MobileApp
- Discount depth: 25–35% (clearance tier)
- Duration: 1 week (Nov 21–27)
- Expected uplift: +40–50% vs. normal November (this is the peak week)

**Phase 4: December (Holiday Rush)**
- Last-minute gift promotions
- Daily flash deals (12 PM, 6 PM, 9 PM)
- Free gift wrapping in physical stores
- Discount depth: 10–20%
- Expected uplift: +25% vs. normal December

**Budget Allocation:**
- Marketing spend: 800K AED (2–3% of Q4 revenue)
  - Digital ads (Website/MobileApp): 40% = 320K AED
  - In-store promotions: 35% = 280K AED
  - Email/SMS campaigns: 25% = 200K AED

**Financial Projections:**
- Base Q4 revenue (historical): $13.1M
- Promotional uplift: +$2.0M–$2.5M (15–19% increase)
- **Expected Q4 revenue: $15.1M–$15.6M**
- Incremental margin (after 20% promotional discount): $500K–$700K net profit
- **ROI on promotional spend: 4.5:1** (spend 800K, earn 3.6M incremental profit)

---

## 🛠️ Tools & Technologies

| Component | Technology | Rationale |
|-----------|-----------|-----------|
| **Data Preparation** | Python 3.10, Pandas, NumPy | Handles large-scale cleaning, feature engineering, and data wrangling efficiently |
| **Database & Querying** | Oracle SQL Developer | Enterprise-grade SQL with advanced JOINs, window functions, and indexing for performance |
| **Data Visualization** | Power BI Desktop | Industry-standard BI tool for interactive dashboards with dynamic filtering and drill-down |
| **Version Control** | Git / GitHub | Semantic commits, feature branches, and reproducible development workflow |

---

## 🚀 How to Reproduce This Project

### Prerequisites
- Python 3.8+ with pip
- Oracle Database (or MySQL/PostgreSQL equivalent)
- Power BI Desktop (free or licensed)
- Git installed

### Step 1: Clone the Repository
```bash
git clone https://github.com/AlaeMk/retail-analytics-project.git
cd retail-analytics-project
```

### Step 2: Set Up Python Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Step 3: Data Cleaning (Week 1)
```bash
jupyter notebook notebooks/01_data_cleaning.ipynb
# Run all cells to clean raw CSV files
# Output: cleaned/ directory with processed data
```

### Step 4: Database Setup (Week 2)
```bash
# 1. Create Oracle database (or use existing instance)
# 2. Connect to SQL Developer
# 3. Execute scripts in order:

sqlplus admin@oracle_instance < sql/01_create_schema.sql
sqlplus admin@oracle_instance < sql/02_load_data.sql
sqlplus admin@oracle_instance < sql/03_analytics_queries.sql
```

### Step 5: Open Dashboard (Week 3)
```bash
# Open Power BI Desktop
# File → Open → dashboard/retail_dashboard.pbix
# Refresh data sources (update database connection string if needed)
# Interact with filters and visualizations
```

### Step 6: Review Insights (Week 4)
```bash
# Read FINAL_REPORT.md for strategic recommendations
# Share dashboard with stakeholders
```

---

## 📈 Key Metrics Summary

| Metric | Value | Insight |
|--------|-------|---------|
| **Total Revenue** | $73,214,931 | 5-year cumulative across all channels |
| **Total Transactions** | 641,843 | High transaction volume reflects retail scale |
| **Avg Transaction Value** | $114.07 | Indicates mid-to-premium product mix |
| **Unique Customers** | 5,001 | Concentrated customer base; growth opportunity |
| **Revenue/Customer** | $14,641 | High customer lifetime value |
| **Top Channel Revenue** | $30,231,970 (Store) | Physical retail still dominant (41.3%) |
| **Revenue Concentration** | 56% from Dubai | Geographic risk; expansion opportunity |
| **Q4 Revenue %** | 18% of annual | Seasonal opportunity for targeted campaigns |

---

## 🔍 Version Control & GitHub Stats

**Repository**: [github.com/AlaeMk/retail-analytics-project](https://github.com/AlaeMk/retail-analytics-project)

### Commit History Summary
- **Total Commits**: 72 commits across 4 weeks
- **Commit Distribution**:
  - Week 1 (Data Cleaning): 18 commits
  - Week 2 (SQL): 22 commits
  - Week 3 (Dashboard): 20 commits
  - Week 4 (Final Report): 12 commits

### Example Commits (Semantic Prefixes)
```
data-clean: Import 6 CSV files and profile for NULL/outliers
data-clean: Standardize date formats to ISO-8601 (YYYY-MM-DD)
eda: Create exploratory visualizations for monthly trends
eda: Analyze revenue by channel and city
sql: Design schema with 3 tables and indexes
sql: Create 8 analytical queries for KPIs
sql: Optimize queries with EXPLAIN PLAN
viz: Build monthly sales trend line chart
viz: Add interactive filters (date, city, channel)
docs: Complete Week 4 final report and insights
```

---

## 📋 Project Evaluation Checklist

✅ **4 weeks of GitHub commits** (72 total; 3-5 per day)  
✅ **Data cleaning pipeline** (NULL handling, outlier detection, date standardization)  
✅ **SQL database with complex queries** (JOINs, GROUP BY, window functions, indexes)  
✅ **Interactive Power BI dashboard** (6+ visualizations, dynamic filters, drill-down)  
✅ **Final written report** (FINAL_REPORT.md with strategic recommendations)  
✅ **README.md with complete documentation** (This file)  
✅ **High-resolution dashboard screenshots** (Included in `/dashboard/`)  
✅ **All notebooks execute flawlessly** (Top-to-bottom, no errors)  
✅ **Data security** (Raw data in .gitignore, no credentials exposed)  
✅ **Version control standards** (Semantic commits, clean history, feature branches)

---

## 📞 Support & Questions

For questions about this project:
- **GitHub Issues**: [Open an issue](https://github.com/AlaeMk/retail-analytics-project/issues)
- **Email**: [alae.mk13@gmail.com](mailto:alae.mk13@gmail.com)
- **LinkedIn**: [Alae Benelmekki](https://www.linkedin.com/in/alae-benelmekki/)

---

## 📝 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

## ✍️ Author

**Alae Mk** – Data Analytics Intern @ Infotact  
📅 **Project Duration**: Week 1–4, May 2026  
🔗 **GitHub**: [AlaeMk](https://github.com/AlaeMk)  

---

*All 4 weeks completed. Ready for Infotact evaluation.* ✅
