# Cyclistic Bike-Share Case Study

## Overview
This case study analyzes historical trip data from **Cyclistic** (Divvy) to understand how **annual members** and **casual riders** use shared bikes differently, and to identify data-driven opportunities to convert casual riders into annual members.

- **Tools & Stack:** Python (`pandas`), Google Colab, GitHub, Tableau Public
- **Dataset Scope:** Consolidated monthly Divvy trip data (`2025-10` to `2026-10`), starting from ~6.94M raw records and refined to ~4.61M records after filtering out missing (`NULL`) station names and invalid/maintenance trips.

---

## Data Cleaning & Methodology
1. **Consolidation & Feature Engineering:**
   - Merged 13 monthly CSV files into a master dataset (`df_all`).
   - Parsed `started_at` and `ended_at` into `datetime` objects and computed `ride_length` (in seconds and minutes) as well as `day_of_week`.
2. **Anomaly & Null Filtering:**
   - Removed invalid trips (`ride_length <= 0`) and internal maintenance/testing trips (`HQ QR`).
   - Excluded records with missing (`NULL` or blank) `start_station_name` or `end_station_name` when evaluating station-level and zone-level metrics (`df_no_null`, ~4.61M rows).
3. **Station Zone Segmentation (`Station_Zone`):**
   - Classified stations using keyword matching into three segments:
     - **Tourist & Lakefront:** Major leisure attractions, parks, beaches, harbors, and lakefront corridors (e.g., *Navy Pier*, *Millennium Park*, lakefront/beach stations).
     - **Commute & Campus:** Financial/business corridors, transit hubs, and universities/colleges.
     - **Other Stations:** Remaining neighborhood and general stations.

---

## Key Findings
- **Casual Riders (Leisure & Lakefront Focus):**
  - Strongly concentrated around waterfront and leisure hubs such as **Navy Pier** (~55k departures), with higher shares of leisure/loop trips and electric bike usage.
- **Annual Members (Routine & Commute Anchor):**
  - Rely more consistently on everyday transit, downtown/corridor routes, and campus areas, reflected in a higher proportion of trips in **Commute & Campus** stations.

---

## Deliverables & Visualizations
- **Analysis Notebook:** [`Case Study - Cyclistic.ipynb`](./Case%20Study%20-%20Cyclistic.ipynb)
- **Tableau Public Dashboard:** *[Add your Tableau Public dashboard link here once published]*

---

## Reproducibility Note
Raw and consolidated CSV files (`divvy_tripdata_clean.csv` and monthly trip files) are excluded from this repository due to file size limits. Place the monthly Divvy CSV files in your Colab/local working directory and run the notebook to reproduce the cleaned dataset and summary tables.
