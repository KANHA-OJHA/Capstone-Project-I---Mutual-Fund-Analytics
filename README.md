# Capstone-Project-I---Mutual-Fund-Analytics
   This repository contains scripts, DAX formulas, and Power BI dashboards for analyzing Mutual Funds Analytics. It covers data cleaning, transformation, and visualization to extract actionable funds insights.

DAY 1 — Project Setup + Data Ingestion (ETL)
Create project folder structure: data/raw, data/processed, notebooks/, sql/, dashboard/, reports/. Initialise Git repo and push to GitHub.
Install all dependencies: pandas, numpy, matplotlib, seaborn, plotly, sqlalchemy, requests, scipy, jupyter. Create requirements.txt.
Load all 10 provided CSV datasets using Pandas. Print .shape, .dtypes, and .head() for each. Note any anomalies.
Fetch live NAV from mfapi.in: GET https://api.mfapi.in/mf/125497 (HDFC Top 100 Direct). Parse JSON response and save as raw CSV.
Fetch NAV for 5 key schemes: SBI Bluechip (119551), ICICI Bluechip (120503), Nippon Large Cap (118632), Axis Bluechip (119092), Kotak Bluechip (120841).
Explore fund master — print unique fund houses, categories, sub-categories, risk grades. Understand AMFI scheme code structure.
Validate AMFI codes — confirm every code in fund_master exists in nav_history. Write a short data quality summary.
Deliverables: data_ingestion.py, live_nav_fetch.py, requirements.txt, GitHub repo with Day 1 commit

Data Cleaning + SQL Database Design
Clean nav_history.csv — parse dates to datetime, sort by amfi_code + date, forward-fill missing NAV for holidays/weekends, remove duplicates, validate NAV > 0.
Clean investor_transactions.csv — standardise transaction_type values (SIP/Lumpsum/Redemption), validate amount > 0, fix date formats, check KYC status enum values.
Clean scheme_performance.csv — validate all return values are numeric, flag anomalies, check expense_ratio range (0.1% – 2.5%).
Design SQLite star schema — write CREATE TABLE statements for dim_fund, dim_date, fact_nav, fact_transactions, fact_performance, fact_aum. Define primary and foreign keys.
Load all cleaned datasets into SQLite — use SQLAlchemy create_engine + df.to_sql(). Verify row counts match source CSVs.
Write 10 analytical SQL queries — top 5 funds by AUM, average NAV per month, SIP YoY growth, transactions by state, funds with expense_ratio < 1%, and 5 more of your choice.
Create data dictionary — document all columns, data types, business definitions, and source references in a Markdown file.
Git commit: "Day 2: Cleaned data + SQLite DB loaded"
Deliverables: 10 cleaned CSVs in data/processed/, bluestock_mf.db, schema.sql, queries.sql, data_dictionary.md
