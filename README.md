Restaurant Chain Sales Analysis (Databricks + Power BI)

An end-to-end analytics project that consolidates 11M+ rows of restaurant order data from multiple file formats, cleans it with SQL on Databricks, stores it as Parquet, and serves it to an interactive Power BI dashboard.

Team project. Built collaboratively. See the "My Contribution" section below.

Data note: (Edit this line) The dataset used here is sample / synthetic data. It does not represent a real company.

Dashboard Preview
<img width="1950" height="807" alt="Flow" src="https://github.com/user-attachments/assets/ef6a1332-dd20-45af-a9f1-51e41bde8a2a" />
<img width="1678" height="937" alt="1" src="https://github.com/user-attachments/assets/60cd6a9f-4138-41d1-8327-0ed8d4726792" />
<img width="1678" height="937" alt="2" src="https://github.com/user-attachments/assets/70ee9481-b767-42ee-aaed-4e3a88c01b0a" />

Architecture
CSV ─┐
Excel ─┤
JSON ─┼──►  Databricks  ──►  SQL cleaning  ──►  Single Parquet file  ──►  Power BI
XML ──┘      (ingest)        (standardize)       (lighter, faster)        (model + DAX + report)
Project Workflow
Data collection: gathered an 11M+ row dataset from multiple sources in different formats (CSV, Excel, JSON, XML).
Ingestion: uploaded all files to Databricks.
Cleaning with SQL: standardized column names and types, handled nulls and duplicates, and unified the schema across sources.
Consolidation: merged the cleaned data into one Parquet file for lighter storage and faster reads.
Connection: connected Power BI to Databricks.
Modeling: built the data model and DAX measures in Power BI.
Reporting: designed the two-page interactive dashboard.
Dashboard Highlights
KPIs: total orders, total sales, average rating.
Sales by branch (6 branches), item, and category.
Orders trend by year (2020 to 2025).
Payment method split (cash, card, wallet).
Branch performance by rating and a detailed branch/category table.
Tech Stack
Layer	Tools
Source formats	CSV, Excel, JSON, XML
Processing & cleaning	Databricks, SQL
Storage format	Parquet
Modeling & visualization	Power BI, DAX
Repository Structure
.
├── README.md
├── sql/
│   └── cleaning_queries.sql
├── notebooks/
│   └── ingestion_and_cleaning.dbc   (or .ipynb / .sql export)
├── powerbi/
│   └── Restaurant_Analysis.pbix
├── images/
│   ├── page1_overview.png
│   ├── page2_branch_details.png
│   └── data_model.png
└── docs/
    └── Restaurant_Analysis.pdf
Data Model

(Add a screenshot of the Model View and list the tables here.)

Table	Type	Description
orders	Fact	Order-level sales, rating, payment method
branches	Dimension	Branch name / location
items	Dimension	Item name and category
date	Dimension	Calendar table
Sample SQL
sql
-- Add your real cleaning queries here, for example:
SELECT DISTINCT
    order_id,
    TRIM(branch)        AS branch,
    CAST(order_date AS DATE) AS order_date,
    CAST(total_price AS DECIMAL(12,2)) AS total_price
FROM raw_orders
WHERE order_id IS NOT NULL;
How to Reproduce
Upload the source files to a Databricks workspace.
Run the notebook/SQL scripts in notebooks/ and sql/ to clean and export the Parquet file.
Open powerbi/Restaurant_Analysis.pbix in Power BI Desktop.
Update the Databricks connection (server hostname, HTTP path, and token) in Data source settings.
Refresh the report.

Never commit access tokens or workspace URLs. Use Power BI parameters or environment variables.

My Contribution

(Edit this section so it matches exactly what you did.)

...
...
...
Author

Mostafa Hamed | Data Analyst LinkedIn | mostafa.hamed1499@gmail.com
