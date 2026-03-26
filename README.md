# 📊 Power BI Project — Sales Data Analysis | ElectroHub

> **A multi-page interactive Power BI dashboard built to analyze retail sales performance across products, cities, promotions, and time periods for a fictional Indian electronics & lifestyle brand — ElectroHub.**

---

## 🗂️ Table of Contents

- [Project Overview](#-project-overview)
- [Dataset Information](#-dataset-information)
- [Tools & Technologies Used](#-tools--technologies-used)
- [Steps Followed](#-steps-followed)
- [Dashboard Pages & Features](#-dashboard-pages--features)
- [Key Insights](#-key-insights)
- [Screenshots](#-screenshots)

---

## 🔍 Project Overview

**ElectroHub** is a multi-category retail store selling products across Electronics, Footwear, Clothing, Home Appliances, Accessories, Kitchenware, Bags, and Personal Care. This Power BI project was built to answer critical business questions around sales performance, profitability, promotion effectiveness, and geographic distribution.

The dashboard enables business stakeholders to:
- Monitor overall sales KPIs at a glance
- Identify top and bottom performing products
- Compare performance across two custom date ranges
- Drill into individual order-level data with dynamic filters
- Understand how promotions drive or dilute revenue

**Project Type:** End-to-End Business Intelligence Dashboard  
**Domain:** Retail / E-Commerce Analytics  
**Geography:** India (15+ major cities)  
**Time Period Covered:** January 2020 – December 2024  
**Total Orders Analyzed:** 3,510

---

## 📁 Dataset Information

The dataset is structured as a **Star Schema** with one fact table and three dimension tables, all stored in a single Excel workbook (`Store_Data.xlsx`).

### Fact Table — `Sheet3` (Transactions)
| Column | Description |
|---|---|
| Date (dd/mm/yyyy) | Transaction date |
| CustomerID | Foreign key to Dim Customers |
| PromotionID | Foreign key to Dim Promotion |
| Product ID | Foreign key to Dim Product |
| Units Sold | Quantity of units purchased |
| Price Per Unit | MRP of the product (INR) |
| Total Sales | Gross revenue before discount |
| Discount Percentage | % discount applied via promotion |
| Discount Value | Absolute discount amount (INR) |
| Net Sales | Revenue after discount (Total Sales − Discount) |

> **Rows:** 3,510 transactions | **Columns:** 10

### Dimension Table — `Dim Customers`
50 unique customers with fields: Customer ID, Customer Name, City, State, Pincode, Email ID, Phone Number

### Dimension Table — `Dim Product`
30 unique products across 8 categories with fields: Product ID, Product Name, Product Line, Price (INR)

### Dimension Table — `Dim Promotion`
5 promotion campaigns with fields: Promotion ID, Promotion Name, Ad Type, Coupon Code, Price Reduction Type

**Promotion Campaigns:**
| Promotion | Discount Type |
|---|---|
| Summer Sale | 20% off |
| Festive Diwali | 10% off |
| New Year Special | 15% off |
| Clearance Sale | 30% off |
| Weekend Flash Sale | 25% off |

---

## 🛠️ Tools & Technologies Used

| Tool | Purpose |
|---|---|
| **Microsoft Power BI Desktop** | Dashboard creation, data modeling, and visualization |
| **Power Query (M Language)** | Data cleaning, transformation, and shaping |
| **DAX (Data Analysis Expressions)** | Calculated columns, measures, KPIs, and dynamic comparisons |
| **Microsoft Excel (.xlsx)** | Raw data source (Star Schema) |
| **OpenStreetMap (via Power BI Maps)** | Geographic visualization of sales by city |

---

## 🪜 Steps Followed

### 1. Data Import & Inspection
- Loaded all four sheets from `Store_Data.xlsx` into Power BI via **Get Data → Excel**
- Previewed data in Power Query to identify data types, nulls, and inconsistencies

### 2. Data Cleaning (Power Query)
- Removed leading/trailing whitespace from text columns (City, State fields in Dim Customers)
- Standardized date format to `dd/mm/yyyy`
- Replaced null values in calculated fields (Price Per Unit, Total Sales, etc.) — confirmed they are derived columns
- Set correct data types for all columns (Date, Whole Number, Decimal, Text)

### 3. Data Modeling
- Established relationships between the Fact table and all three Dimension tables using foreign keys
- Configured a **Star Schema** with one-to-many relationships
- Ensured correct cross-filter direction for all relationships

### 4. DAX Measures & Calculated Columns
Key measures created:
- `Total Sales` — Sum of Net Sales
- `Total Profit` — Derived from Net Sales and cost basis
- `Total Quantity Sold` — Sum of Units Sold
- `Total Orders` — Count of distinct Order IDs
- `Average Discount` — Average discount by Promotion Category
- `Sales 1 / Sales 2` — Dynamic measures for period comparison using two independent date slicers
- `Profit 1 / Profit 2` — Same pattern for profit comparison
- `Quantity 1 / Quantity 2` — Same pattern for quantity comparison

### 5. Dashboard Design (4 Report Pages)
Designed and built four interactive report pages, each serving a distinct analytical purpose (detailed below).

### 6. Interactivity & UX
- Added **Edit Interactions** to control how visuals filter each other across the page
- Configured two **independent date slicers** (Date Filter 1 & Date Filter 2) on the Comparison page that do NOT interact with each other — enabling true period-over-period comparison
- Applied **visual-level filters** and **slicer panels** (Date, Customer Name, Product Name, Promotion Name) on the Table Visual page
- Used consistent color theme: **purple/lavender** for primary metrics and **pink/magenta** for secondary/comparison metrics

### 7. Publishing & Documentation
- Saved final report as `Power_BI_Project_-_Sales_Data_Analysis.pbix`
- Captured screenshots for all 4 dashboard pages for documentation

---

## 📄 Dashboard Pages & Features

### Page 1 — Overview
A high-level summary dashboard with four visual components:
- **Sales by City (Map Visual):** Bubble map of India showing sales volume across 15+ cities including Mumbai, Delhi, Bangalore, Chennai, Pune, Kolkata, and more
- **Number of Orders (Card):** Displays total order count — **3,510 orders**
- **Average Discount by Promotion Categories (Bar Chart):** Horizontal bar chart showing average discount per promotion type
- **Profit vs Net Sales (Scatter Plot):** Visualizes the strong positive correlation between profit and net sales across all products
- **Sales Trends by Period (Line/Dot Chart):** Time-series chart spanning 2020–2024 showing daily/weekly sales fluctuations with annotated peaks

### Page 2 — Top & Bottom 5 Analysis
Six side-by-side bar charts revealing the best and worst performing products:
- **Top 5 / Bottom 5 by Sales** (revenue in INR)
- **Top 5 / Bottom 5 by Quantity Sold** (units)
- **Top 5 / Bottom 5 by Profit** (INR)

### Page 3 — Comparison: Sales, Profit & Quantity
A period-over-period comparison tool built with dual independent slicers:
- **Date Filter 1** (purple) and **Date Filter 2** (pink/red) — each controls its own set of KPI bar charts
- Three grouped bar charts: **Total Sales**, **Total Profit**, **Total Quantity Sold**
- Each chart shows two bars (Period 1 vs Period 2) for direct comparison
- Edit Interactions configured so both slicers operate independently

### Page 4 — Table Visual (Drill-through)
A detailed, filterable order-level data table for granular analysis:
- **Columns:** CustomerID, Order ID, Product ID, PromotionID, Date, Discount, Discount %, Net Sales, Price Per Unit, Profit, Total Sales, Units Sold
- **Slicers:** Date, Customer Name, Product Name, Promotion Name (all set to "All" by default)
- Enables precise lookup and auditing of individual transactions

---

## 💡 Key Insights

### Sales Performance
- **Total Revenue:** ₹122M across 3,510 orders (Jan 2020 – Dec 2024)
- **Total Profit:** ₹12.2M — indicating an approximately **10% overall profit margin**
- **Total Units Sold:** 7,100+ units across all categories

### Product Performance
- **Apple iPhone 14** dominates all three performance metrics — ranked #1 in Sales (₹21.4M), Quantity (281 units), and Profit (₹2.14M)
- **Apple MacBook Air** and **Sony Bravia 55" TV** rank 2nd and 3rd in both Sales and Profit, confirming Electronics as the highest-revenue category
- **Colgate Toothpaste** has the lowest sales (₹0.02M) and profit (₹2K), suggesting Personal Care products have limited revenue impact
- The top 5 products are all Electronics, while the bottom 5 are from Personal Care and Kitchenware — a clear signal for inventory and marketing prioritization

### Promotion Effectiveness
- **Weekend Flash Sale** offers the highest average discount (₹23K), making it the most aggressive promotion
- **Clearance Sale** follows at ₹18K average discount
- **Festive Diwali** offers the lowest discount (effectively ₹0K average), suggesting it drives engagement through other means
- High discounts in Weekend Flash Sale and Clearance Sale may be worth reviewing for margin impact

### Geographic Distribution
- Sales are concentrated in major metro areas: **Mumbai, Delhi, Pune, Bangalore, Kolkata, Chennai**
- Northern India (Delhi, Jaipur, Kanpur, Lucknow, Patna) shows a strong cluster of activity
- Tier-2 cities like Nagpur, Indore, Visakhapatnam, and Bhopal also show meaningful order volumes

### Profit vs Sales Relationship
- The scatter plot reveals a **strong positive linear correlation** between profit and net sales
- Higher-priced electronics products (with values above ₹20K profit) generate disproportionately higher net sales (above ₹200K), confirming premium product focus is financially sound

### Sales Trends Over Time
- Peak sales reached **₹0.65M** in a single period (mid-2023), the highest across all years
- **2020** shows an early spike of ₹0.55M followed by normalization, possibly reflecting initial launch momentum
- Sales trends show **consistent volatility** with periodic spikes, likely aligned with promotion periods
- The comparison page (Page 3) allows any two custom periods to be benchmarked side-by-side in real time

---

## 📸 Screenshots

### Page 1 — Overview Dashboard
![Overview](<img width="1253" height="707" alt="Image" src="https://github.com/user-attachments/assets/01633a41-c4a9-44f0-aded-fd20848ba4e3" />)
> Displays the India sales map, order count card, average discount by promotions, profit vs. net sales scatter, and full sales trend timeline (2020–2024).

---

### Page 2 — Top & Bottom 5 Product Analysis
![Top Bottom 5 Analysis](<img width="1282" height="722" alt="Image" src="https://github.com/user-attachments/assets/6436cf95-e6e0-4f3b-a075-79232887cfb3" />)
> Six bar charts ranking the top and bottom 5 products by Sales, Quantity Sold, and Profit.

---

### Page 3 — Period Comparison (Sales / Profit / Quantity)
![Comparison Sales Profit Quantity](<img width="1285" height="722" alt="Image" src="https://github.com/user-attachments/assets/4f5a490c-5da5-4599-a532-06c5d1c99ae5" />)
> Dual date slicer comparison view showing Sales 1 vs Sales 2, Profit 1 vs Profit 2, and Quantity 1 vs Quantity 2 for any two user-selected time windows.

---

### Page 3 — Edit Interactions Configuration
![Edit Interactions](<img width="1281" height="726" alt="Image" src="https://github.com/user-attachments/assets/cf59f06b-84f4-4835-8575-73f7d964e00c" />)
> Demonstrates how Date Filter 1 (orange) and Date Filter 2 (pink) are configured to control separate sets of visuals independently, preventing cross-slicer interference.

---

### Page 4 — Detailed Table Visual
![Table Visual](<img width="1287" height="722" alt="Image" src="https://github.com/user-attachments/assets/d33ec5e6-37b2-4e59-9763-c65162859fff" />)
> Granular order-level table with dynamic slicers for Date, Customer Name, Product Name, and Promotion Name.

---
