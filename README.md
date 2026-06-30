# VoltEdge Systems: End-to-End Sales Performance & Customer Lifetime Value Project

## 📌 Project Overview
This repository contains an end-to-end data analytics project focused on **VoltEdge Systems**, an industrial IoT and component provider. Utilizing a relational database schema (Snowflake/SQL) and **Tableau**, this project uncovers revenue drivers, identifies high-value customer segments, tracks purchasing frequencies, and surfaces optimization lists for target marketing.

📊 **[Link to Interactive Tableau Public Dashboard](https://public.tableau.com/app/profile-settings#:~:text=https%3A//public.tableau.com/app/profile/josephine.lawal)**

---

## 🛠️ Tech Stack & Tools
* **Data Warehousing / SQL:** Snowflake (Warehousing, schema design, subqueries, CTEs, Window Functions)
* **BI & Data Visualization:** Tableau Desktop 
* **Data Layer:** 5 Relational CSV tables (`Customer`, `Product`, `ProductLine`, `Order`, `OrderLine`)

---

## 📐 Data Architecture & Ingestion
The database structure adheres to strict relational dependencies. Data must be ingested in the following exact sequence to preserve entity-relationship integrity:
1. `ProductLine` ➡️ 2. `Product` ➡️ 3. `Customer` ➡️ 4. `Order` ➡️ 5. `OrderLine`

---

## 💡 Key Business Questions & SQL Insights

### 1. High-Value Customer Segmentation (RFM / Spend Analysis)
Using windowing functions and custom conditional logic, customers were grouped by lifetime spend to identify enterprise vs. small-scale clients.
* **SQL Highlight:** Calculated moving cumulative spending and bucketed clients using `CASE WHEN` spending brackets (High Value > $55k, Medium Value $20k–$55k, Low Value).

### 2. Strategic Inventory & Revenue Engines
* Isolated the top 10 revenue-generating products using CTE aggregations.
* Evaluated which product lines (e.g., *Apex Collection*) outperform in volume using window functions (`RANK()`, `DENSE_RANK()`, `ROW_NUMBER()`).

### 3. Leakage & Risk Mitigation
* Formulated `LEFT JOIN` algorithms to extract registered customers who have **never placed an order**. This serves as a target re-engagement pipeline for marketing teams.

---

## 📊 Tableau Dashboard Storyboard & Visualizations

The final interactive dashboard consists of three strategic lenses:

### 🏙️ 1. Executive Revenue Command
* **Objective:** Instantly reveal top-line earnings, order velocities, and dominant product finishes.
* **Key Visuals:** Product Line TreeMap, Top 10 Products horizontal sorted bar chart.

### 👥 2. Customer Cohort & Geography Map
* **Objective:** Map spatial distribution of sales density and client tiers.
* **Key Visuals:** Filled USA map scaled by invoice size, Packed bubble chart segmenting Value categories.

### 📦 3. Operational Basket Analysis
* **Objective:** Audit the quantity complexity per order tracking logistics and shipping burdens.
* **Key Visuals:** Chronological line chart over time, Order frequency breakdown.

---

## 🚀 How to Run this Project Locally
1. Clone the repository: `git clone https://github.com/YOUR_USERNAME/VoltEdge-Sales-Analytics.git`
2. Create your database schema using the instructions inside `sql/database_setup.sql`.
3. Import the CSV files from the `/data` folder into your database following the numbered sequence.
4. Execute `sql/business_queries.sql` to verify analytical metrics.
5. Open the `.twbx` file inside the `/tableau` folder via Tableau Desktop or Tableau Public to explore the interactive visual layer.# VoltEdge-Sales_Analytics
