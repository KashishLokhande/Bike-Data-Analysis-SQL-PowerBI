# Bike Shop Analysis Project

This project analyzes the sales and profitability data for a bike shop over a two-year period using SQL and Power BI. The objective was to identify trends, generate insights, and recommend strategies for pricing and profitability improvements.

## Project Overview

The analysis covered two years of data from the `bike_share_yr_0` and `bike_share_yr_1` tables, as well as a `cost_table` detailing costs and pricing. SQL was used to clean and merge the data, while Power BI was used to visualize key metrics and create an interactive dashboard.

---

## Dashboard Preview

Below is a preview of the dashboard created for the Bike Store project:

![Dashboard Preview](file:///C:/Users/HOME/Downloads/BIKE%20SALES%20PROJECT/Bike-Data-Analysis-SQl-PowerBI--main/Bike-Data-Analysis-SQl-PowerBI--main/Image%201%20.png)

![Dashboard Preview](file:///C:/Users/HOME/Downloads/BIKE%20SALES%20PROJECT/Bike-Data-Analysis-SQl-PowerBI--main/Bike-Data-Analysis-SQl-PowerBI--main/Image%202.png)

## Tools and Technologies

- **SQL**: For data cleaning, transformation, and analysis.
- **Power BI**: For data visualization and dashboard creation.

---

## Steps in the Project

1. **Data Preparation in SQL:**
   - Combined data from `bike_share_yr_0` and `bike_share_yr_1` using a `UNION ALL` query.
   - Joined the combined dataset with the `cost_table` to calculate revenue and profit.
   - Calculated the following metrics:
     - **Revenue**: `riders * price`
     - **Profit**: `revenue - COGS`

   Example SQL Query:
   ```sql
   WITH cte AS (
       SELECT * FROM bike_share_yr_0
       UNION ALL
       SELECT * FROM bike_share_yr_1
   )
   SELECT 
       dteday, season, a.yr, weekday, hr, rider_type, riders, price, COGS,
       riders * price AS revenue,
       (riders * price) - (riders*COGS) AS profit
   FROM cte AS a
   LEFT JOIN cost_table AS b 
   ON a.yr = b.yr;
   ```

2. **Exporting Results:**
   - Exported SQL query results to a CSV file for use in Power BI.

3. **Visualization in Power BI:**
   - Created an interactive dashboard with the following elements:
     - **KPI Metrics:** Total riders, total revenue, and total profit.
     - **Revenue and Profit Over Time:** A bar and line chart showing trends over two years.
     - **Revenue by Season:** Bar chart visualizing revenue per season.
     - **Riders Demographics:** A donut chart showing the proportion of casual vs. registered users.
     - **Revenue by Hour:** A heatmap showing revenue across different hours and days of the week.

---

## Key Findings

1. **When Are We Making Money?**
   - Peak earnings occur during early evening hours, specifically between 5:00 PM and 7:00 PM, with combined revenue of $2.98M ($1.55M in the 5 PM hour and $1.43M in the 6 PM hour).
   - Each peak hour earns about $1.49M, roughly 2.4× the average hour ($0.63M).

2. **Revenue by Season:**
   - Season 3 generated the highest revenue (~$4.9M), followed by Season 2 (~$4.2M).

3. **Rider Demographics:**
   - Registered users contribute ~81.26% of total revenue.
   - Registered riders generate ~4.3× more total profit than casual riders ($8.49M vs $1.96M), but profit per ride is almost identical ($3.18 vs $3.16). The gap comes from volume, not margin.

4. **KPI Summary:**
   - Total Riders: 3.29 Million
   - Total Revenue: $15.19 Million
   - Total Profit: $10.45 Million (~69% margin)
   - Profit by year: $3.42M in year 0 and $7.03M in year 1.

3. Section "Recommendations"
---

## Recommendations

1. **Conservative Price Increase:**
   - A 10-15% price increase is recommended to test the market's response without risking significant loss of customers.
   - For example:
     - A 10% increase would raise the price from $4.99 to $5.49.
     - A 15% increase would set the price at approximately $5.74.

2. **Segmented Pricing Strategy:**
   - Introduce separate pricing strategies for casual and registered riders based on their sensitivity to price changes.
   - Offer membership perks to convert high-usage casual riders to the registered category.

3. **Monitor and Adjust:**
   - Monitor customer feedback and sales data closely after implementing price changes to make necessary adjustments.

4. **Focus on Peak Hours:**
   - Optimize staffing, inventory, and marketing spend during peak revenue hours (5:00 PM to 7:00 PM).
   - Monetize high-demand hours through dynamic pricing, as a way to raise revenue in the busiest hours.
---

## Files in the Repository

| File | Description |
|------|-------------|
| `bike_share_yr_0.csv`, `bike_share_yr_1.csv` | Raw yearly datasets |
| `cost_table.csv` | Cost & pricing table |
| `Cleaned_data.csv` | Final cleaned dataset |
| `SQL Query.sql` | SQL transformation logic |
| `Bike Data Analysis.pbix` | Power BI dashboard |
| `Dashboard.png`, `Cycle Imge.png` | Dashboard preview screenshots |
| `README.md` | Documentation |


---

## Conclusion

This project provides actionable insights into the bike shop's performance and offers strategies to enhance revenue and profitability. The interactive dashboard allows stakeholders to explore data trends and make data-driven decisions effectively.

