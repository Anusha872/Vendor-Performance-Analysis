# Vendor-Performance-Analysis


An end-to-end data analytics project utilizing Python for data engineering and transformation, a local SQLite relational environment, and an interactive Google Looker Studio dashboard to track vendor metrics.

## Executive Performance Dashboard
![Dashboard Final View](Dashboard.png)

## Data Pipeline Tech Stack
* **Language:** Python 3 (Pandas, SQLAlchemy)
* **Storage Environment:** SQLite Database
* **BI Presentation:** Google Looker Studio
* **Core Metrics Tracked:** Total Sales Volume ($), Net Purchase Contributions, Margin Profiles, Stock Inventory Turnovers


## The Data  Pipeline (ETL)

### 1. Extract & Load (`get_vendor_summary.py`)
To prevent system memory (RAM) crashes when handling heavy, multi-million row transaction files, the ingestion pipeline utilizes **Production Safe Chunking**. 
* Reads raw transactional data in controlled blocks using `chunksize=100000`.
* Streams chunks smoothly into a localized SQLite relational environment (`inventory.db`).
* Implements background **Audit Logging** (`ingestion_db.log`) to log database events and isolate runtime database errors automatically.

### 2. Transform & Analyze (`Vendor Performance Analysis.ipynb`)
Using a Jupyter Notebook environment, SQL queries and Pandas tag-team to extract deep business insights from the relational structure:
* **SQL Queries:** Executed multi-table structural `JOIN` operations to map historical customer sales against inventory levels and vendor invoices.
* **Pandas Transformations:** Applied programmatic vector operations to clean up inconsistent text inputs, scrub null values, and calculate financial percentages.

---

## 🔍 Core Business Problems Solved

### Identifying "Shelf-Warmers" (Inventory Optimization)
Calculated the **Stock Turnover Rate** by combining current inventory levels with transaction frequencies to flag which vendor items are taking up expensive warehouse capital without converting to active sales.

### Catching Vendor Overcharges (Cost Leakage)
Engineered a data matching script that flags transactions where the actual purchase price exceeded agreed wholesale contract limits, saving the company from margin leakage.

### Margin Analysis for Executives
Aggregated and isolated low-performing product clusters by plotting product profit margins against gross revenues on dynamic scatter plots.

---

## 🗄️ Repository Directory Layout
* `my_data_project/data/get_vendor_summary.py` -> The automated Python data loading engine.
* `my_data_project/data/Vendor Performance Analysis.ipynb` -> Interactive SQL & Pandas analytics notebook.
* `Dashboard.png` -> High-resolution dashboard screenshot for executive reporting.
* *Note: Raw data spreadsheets (`.csv`) and database binaries (`.db`) are excluded via `.gitignore` to maintain system optimization and security compliance.*



