# DMR BIKE SHOP — Power BI & SQL Dashboard

This project showcases a full-stack analytics dashboard built in **Power BI**, powered by structured **SQL transformations**. It was developed as a learning exercise and portfolio piece, inspired by a publicly available tutorial. All logic and enhancements were created independently by **Darnell Riel**.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools Used](#tools-used)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References & Attribution](#references--attribution)
- [Disclaimer](#disclaimer)

---

## Project Overview

This dashboard analyzes bike shop performance across:
- Hourly profitability
- Seasonal revenue trends
- Rider demographics
- Year-over-year KPIs

It emphasizes SQL logic, interactive storytelling, and visual clarity using Power BI.

---

## Data Source

The dataset is simulated and includes:
- Hourly rider logs across two years
- Rider type (registered vs casual)
- Seasonal and weekday breakdowns
- Pricing and cost data per rider

---

## Tools Used

- **Power BI Desktop** for dashboard creation and visualization
- **SQL** for data transformation and modeling
- **DAX** for calculated measures and dynamic KPIs
- **Excel** for initial inspection and formatting

---

## Data Cleaning and Preparation

- Combined multi-year datasets using `UNION ALL`
- Applied `LEFT JOIN` to merge cost data
- Created calculated columns for revenue and profit
- Standardized date formats and categorical labels

> Sample SQL logic:
```sql
WITH cte AS (
  SELECT * FROM bike_share_yr_0
  UNION ALL
  SELECT * FROM bike_share_yr_1
)
SELECT 
  dteday, season, a.yr, weekday, hr, rider_type, riders, price, COGS,
  ROUND(riders * price, 2) AS revenue,
  ROUND(riders * price - COGS*riders, 2) AS profit
FROM cte a
LEFT JOIN cost_table b ON a.yr = b.yr;
```

## Exploratory Data Analysis

Initial exploration focused on:

- Rider distribution by hour and season  
- Profitability trends across weekdays  
- Comparison of registered vs casual rider behavior  

---

## Data Analysis

Key metrics derived using SQL and DAX:

- Revenue and profit per hour  
- Profit margin by season  
- Rider type segmentation  
- Year-over-year performance comparison  

---

## Key Insights

The results are summarized as follows:

- **Peak Hours**: Highest revenue and profit occur between **10 AM–3 PM** and **5–6 PM**  
- **Seasonal Revenue**: Spring and summer months show strong performance, with over **₱4.9M** in peak season  
- **Rider Breakdown**: Registered riders make up **81.17%**, while casual riders account for **18.83%**  
- **Profit Margin**: Average profit margin across all hours and seasons is approximately **45%**  

---

## Recommendations

- Target marketing during peak hours and seasons  
- Offer incentives to casual riders to boost conversion  
- Optimize pricing and cost structure during low-profit hours  

---

## Limitations

- Dataset is simulated and may not reflect real-world variability  
- Static breakdowns for season, rider type, and time of day (only year is interactive)  
- External factors (weather, holidays) not included in analysis  

---

## References & Attribution

This project was inspired by a publicly available Power BI tutorial.  
All SQL logic and enhancements were created independently by **Darnell Riel** for portfolio purposes.

---

## Power BI Features

- Interactive slicer for filtering by **year**  
- Custom DAX measures for dynamic profit margin calculations  
- Drill-through pages to explore hourly and seasonal performance  
- Conditional formatting to highlight peak metrics  
- Tooltips that provide contextual insights on hover  

---

## Dashboard Visual

![Screenshot – DMR BIKE SHOP Dashboard](https://github.com/user-attachments/assets/15da3b88-dd74-4c7d-9586-9af73cfe5892)

---

## Disclaimer

This dashboard is intended for portfolio purposes only.  
The data used is either simulated or anonymized and does not represent actual business performance.  
All insights are illustrative and should not be used for commercial decision-making.
