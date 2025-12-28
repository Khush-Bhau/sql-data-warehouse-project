 # SQL Data Analytics Project

 Professional README — Data Analytics & Reporting (SQL)

 ## Overview

 This folder contains focused analytics and reporting artifacts that run on top of the data warehouse. The goal is to provide a reproducible set of SQL queries and example outputs that deliver business insights (customer behaviour, product performance, sales trends) using the transformed `Gold` tables produced by the warehouse project.

 ## Scope

 - Exploratory analysis and descriptive metrics implemented as SQL scripts.
 - Reusable report queries intended for use in BI tools (Power BI, Tableau) or as CSV exports.
 - Separation of concerns: all ETL and schema management live in `../sql-data-warehouse-project`; this folder consumes the warehouse outputs.

 ## Prerequisites

 - A running SQL Server instance (Local or remote) with access credentials.
 - The data warehouse populated with Gold-layer tables. You can restore the provided backup `datasets/DataWarehouseAnalytics_Backup.bak` or run the warehouse ETL first.
 - A SQL client (SSMS, Azure Data Studio) or `sqlcmd` to run the scripts.

 ## Quick start

 1. Restore the backup (optional):

    - In SSMS: Right-click Databases → Restore Database → select `DataWarehouseAnalytics_Backup.bak` from `datasets/`.
    - Or use `sqlcmd` to run `scripts/00_init_database.sql` which contains database creation and initialisation statements.

 2. Run the analytics scripts in the order below (recommended order listed in `scripts/`):

    - `00_init_database.sql` — creates the target database and helper objects used by analysis scripts.
    - `01_database_exploration.sql` — inventory of tables, row counts, and quick sanity checks.
    - `02_dimensions_exploration.sql` — checks and samples for dimension tables (customers, products).
    - `03_date_range_exploration.sql` — inspects date coverage and missing periods.
    - `04_measures_exploration.sql` — computes core business measures (sales, revenue, counts).
    - `05_magnitude_analysis.sql` — identifies top contributors and distribution of measures.
    - `06_ranking_analysis.sql` — ranking queries for top customers/products/regions.
    - `07_change_over_time_analysis.sql` — period-over-period changes and growth rates.
    - `08_cumulative_analysis.sql` — running totals and cumulative metrics for trend charts.
    - `09_performance_analysis.sql` — performance KPIs and efficiency metrics.
    - `10_data_segmentation.sql` — segmentation (RFM, cohorts) examples for customer grouping.
    - `11_part_to_whole_analysis.sql` — contribution-to-total queries for pie/stacked visuals.
    - `12_report_customers.sql` — example reporting dataset for customer-focused dashboards.
    - `13_report_products.sql` — example reporting dataset for product-focused dashboards.

 3. Export results to CSV or connect Power BI directly to the database for visualizations. Example output CSV files are present under `datasets/csv-files/gold/` (e.g. `gold.dim_customers.csv`, `gold.fact_sales.csv`).

 ## Folder structure (key files)

 - `scripts/` — SQL scripts for exploration and report preparation.
 - `datasets/` — packaged example datasets and a backup file (`DataWarehouseAnalytics_Backup.bak`).
 - `docs/` — diagrams and the project data catalog (`data_catalog.md`) and naming conventions.

 ## Design notes and best practices

 - This project uses the Medallion pattern (Bronze / Silver / Gold). Analytics scripts assume the `Gold` layer contains cleaned, business-ready tables.
 - Scripts are idempotent where practical — use `BEGIN TRAN` / `ROLLBACK` patterns in development to avoid accidental changes.
 - Keep heavy aggregations as materialized views or pre-computed tables if running in a production-like environment to improve dashboard performance.

 ## Recommendations to improve reproducibility (optional but recommended)

 - Add a short `docs/repro.md` with exact commands to restore the backup and run scripts.
 - Add a `notebooks/` folder with 1–2 Jupyter notebooks showcasing EDA and a sample Power BI export flow.
 - Provide a `results/` folder with final CSVs or sample dashboard screenshots used in presentations.

 ## Reporting guidance

 - For dashboards, use the `report_customers` and `report_products` scripts as the base datasets: they are shaped for slicers and visual filters.
 - Use `03_date_range_exploration.sql` and `07_change_over_time_analysis.sql` to build time intelligence measures (YTD, MTD, rolling windows).

 ## Contact & license

 Author: Khush Agrawal

 License: MIT — see root `LICENSE`.

 ## Questions / Contributions

 If you want, I can:

 - Convert one or two scripts into parameterized views or stored procedures for easier reuse.
 - Add a `docs/repro.md` with exact `sqlcmd` or PowerShell commands to restore the backup and run all scripts end-to-end.

 ---
# sql-data-analytics-project
A comprehensive collection of SQL scripts for data exploration, analytics, and reporting. These scripts cover various analyses such as database exploration, measures and metrics, time-based trends, cumulative analytics, segmentation, and more.
This repository contains SQL queries designed to help data analysts and BI professionals quickly explore, segment, and analyze data within a relational database. Each script focuses on a specific analytical theme and demonstrates best practices for SQL queries.

---

## 🛡️ License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and share this project with proper attribution.

🌟 About Me
Hi there! I'm Khush Agrawal.
I’m a passionate CS (Data Science) student, technical club member, and aspiring Business Analyst / Data Analyst on a mission to turn data into decisions and build a high-impact career in analytics.

I love exploring data, solving real-world problems, and sharing insights that help others grow. When I’m not in front of a screen, you’ll find me playing volleyball, exploring nature, or leveling up my skills for the next big opportunity.

Let’s connect and grow together! 🚀

[LinkedIn](www.linkedin.com/in/khush-agrawal007)
