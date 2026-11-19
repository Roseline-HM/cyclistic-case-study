# Cyclistic Bike-Share Case Study

## Overview
This case study analyzes historical trip data from **Cyclistic** (Divvy) to understand how **annual members** and **casual riders** use shared bikes differently, and to provide data-driven marketing recommendations to convert casual riders into annual members.

- **Tools & Stack:** Python (`pandas`), Google Colab, GitHub, Tableau Public
- **Timeframe:** 13-month window (`2025-10` to `2026-10`, 13 monthly CSV datasets)
- **Live Interactive Dashboard:** [View on Tableau Public](https://public.tableau.com:9443/views/CaseStudy-Cyclistic_17950645437570/Trips_by_Zone?:language=fr-FR&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
- **Repository:** [Roseline-HM/cyclistic-case-study](https://github.com/Roseline-HM/cyclistic-case-study/tree/main)

---

## Data Cleaning & Methodology
1. **Consolidation & Feature Engineering:**
   - Consolidated 13 monthly Divvy CSV files totaling **6,940,490** raw records.
   - Parsed `started_at` and `ended_at` timestamps and engineered `ride_length` (in seconds and minutes) and `day_of_week` (`1 = Sunday` to `7 = Saturday`).
2. **Two-Tier Quality & Null Filtering:**
   - **Global Clean Dataset (`df_clean` — 6,940,461 rows):** Removed **29 invalid records** (`ride_length <= 0` seconds and internal maintenance/test trips `HQ QR`) for overall volume, duration, and temporal analyses.
   - **Station-Complete Dataset (`df_no_null` — ~4.61M rows):** Filtered out records with missing (`NULL` or blank) `start_station_name` or `end_station_name` (largely dockless electric bike drop-offs) to ensure accurate station, route, and zone metrics.
3. **Station Zone Segmentation (`Station_Zone`):**
   - Categorized stations via keyword matching into three segments:
     - **Tourist & Lakefront:** Major attractions, parks, beaches, harbors, and lakefront corridors (e.g., *Navy Pier*, *Millennium Park*, *DuSable Lake Shore Dr*).
     - **Commute & Campus:** Financial/downtown corridors, rail/transit hubs, and universities/colleges.
     - **Other Stations:** Remaining residential and neighborhood stations.

---

## Key Analytical Findings
- **Trip Volume & Duration:** Annual members generate higher overall trip volume (~4.48M trips vs. ~2.46M for casual riders) with shorter, routine rides (**12.28 min** mean / **8.49 min** median), whereas casual riders take significantly longer leisure rides (**20.17 min** mean / **10.69 min** median).
- **Weekly & Seasonal Patterns:** Members ride consistently during workdays (peaking Tuesday–Thursday at >700k trips/day) and remain resilient in winter (>112k trips/month in Dec–Jan). Casual usage surges on weekends (peaking Saturday at **526,624** trips) and during warm summer months (peaking July at **357,779** trips).
- **Spatial Concentration & Loop Trips:** Casual activity clusters heavily around lakefront landmarks—led by **Navy Pier** (>55,700 departures)—with high rates of round-trip **loop rides** (*Navy Pier → Navy Pier* >10,700 trips). Members anchor around transit hubs (*Canal St & Madison St*, *Clinton St & Washington Blvd*) and academic campuses (*University Ave & 57th St*).
- **Bike Type Preference:** Both groups strongly prefer **electric bikes** over classic bikes (~4.97M electric trips vs. ~1.97M classic trips overall).

---

## Top 3 Recommendations (Act Phase)
1. **Seasonal & Weekend Conversion Campaigns at Lakefront Hubs:** Deploy QR-code signage and post-ride in-app prompts at top recreational hubs (*Navy Pier*, *DuSable Lake Shore Dr & Monroe St*, *Millennium Park*) between May and September, showing casual weekend riders how quickly multi-ride or day passes pay for an annual membership.
2. **E-Bike & Extended-Ride Membership Bundle:** Introduce a first-year annual membership incentive featuring discounted e-bike unlock/minute credits to appeal directly to casual riders' preference for electric bikes and longer ~20-minute rides.
3. **Geo-Targeted Offers for Repeat Casual Riders Near Transit & Campus Corridors:** Target casual riders taking repeat point-to-point trips near **Commute & Campus** stations with weekday commuter messaging and seasonal transition discounts in late summer/early autumn.

---

## Deliverables & Reproducibility
- **Jupyter / Colab Notebook:** [`Case Study - Cyclistic.ipynb`](./Case%20Study%20-%20Cyclistic.ipynb)
- **Interactive Dashboard:** [Tableau Public — Cyclistic Case Study](https://public.tableau.com:9443/views/CaseStudy-Cyclistic_17950645437570/Trips_by_Zone?:language=fr-FR&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

*Note: Raw and consolidated CSV datasets (`divvy_tripdata_clean.csv`) are excluded from this repository due to GitHub file size limits. Place the 13 monthly Divvy CSV files in your working directory and run the notebook to reproduce all tables and exports.*
