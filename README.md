# 🏙️ Bengaluru Civic Efficiency Tracker 

![Python](https://img.shields.io/badge/Python-3.12-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data_Cleaning-green)
![SQLite](https://img.shields.io/badge/SQLite-In_Memory_Engine-lightgrey)

An open-source data engineering pipeline analyzing over 120,000+ live civic complaints in Bengaluru to measure municipal efficiency, track backlog resolution, and celebrate the city's top-performing wards.

## Project Overview
While public civic discourse often focuses on unresolved issues, this project takes a **Constructive Data Narrative** approach. By analyzing the 2025 Bruhat Bengaluru Mahanagara Palike (BBMP) dataset, this pipeline reveals that over **109,000 complaints** have been successfully closed this year, and highlights the specific neighborhoods clearing their backlogs the fastest.

## The Data Pipeline Architecture

This project currently operates via a robust 3-stage data engineering methodology:

### 1. Data Extraction
* Ingested the live 2025 BBMP Grievance dataset (17MB+ CSV) directly into memory using Python `requests` and `io`.

### 2. Data Transformation & Cleaning (Pandas)
* **Null Handling:** Dropped records with missing critical spatial data.
* **Text Standardization:** Applied `.str.strip().str.title()` to uniformize inconsistent human data entry.
* **Synonym Mapping:** Engineered a custom mapping dictionary to unify fragmented categories (e.g., merging "Pot hole" and "Pothole").
* **Temporal Parsing:** Coerced messy string dates into calculated Datetime objects for time-series analysis.

### 3. Database & SQL Analysis (SQLite3)
* Spun up an in-memory SQLite database to prevent local overhead.
* Engineered complex SQL queries using `GROUP BY`, `CASE WHEN`, and `HAVING` clauses to calculate precise **Resolution Rates** per ward.
* Handled real-world data edge cases by mathematically filtering out anomalies (wards with < 100 complaints) and unstructured buckets (`Non Ward`).

## Key Insights (Current Data)
* **Total Volume:** Over 120,000 civic complaints logged.
* **Resolution Scale:** Over 109,000 issues successfully completely and closed by civic workers.
* **Top Performers:** SQL analysis dynamically identifies the Top 10 wards with the highest statistical resolution rates in the city.

## Repository Structure
* `cleaning_pipeline.ipynb`: The Colab notebook containing the raw extraction, Pandas transformation, and SQL engine.
* `bbmp_clean_2025.csv`: The sanitized dataset exported from the pipeline.

---
*Built in public to bring transparent, constructive data to civic infrastructure. Interactive web visualization coming soon!*
