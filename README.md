# Game Zone Data Analytics Project

## Data Cleaning Report

### Overview

The data cleaning phase aimed to prepare the Game Zone orders dataset for analysis. I followed the **CLEAN** framework: Conceptualize, Locate issues, Evaluate unsolvable problems, Augment the data, and Note/document all steps.

---

### 1. Conceptualize the Data

- Loaded the raw dataset from Excel.
- Inspected the data structure (`df.info()`), noting ~22,000 orders and key columns such as `ORDER_ID`, `USER_ID`, `USD_PRICE`, `PURCHASE_TS`, `SHIP_TS`, `PRODUCT_NAME`, `MARKETING_CHANNEL`, and `COUNTRY_CODE`.
- Identified `USD_PRICE` as the main metric for analysis.
- Flagged columns needing type conversion (e.g., `PURCHASE_TS` to datetime).

---

### 2. Locate and Fix Issues

#### **User and Order IDs**

- Checked uniqueness of `USER_ID` and found ~91% unique users.
- Detected 145 duplicate `ORDER_ID`s, investigated them, and confirmed they were exact duplicates.
- Removed duplicate orders to ensure data integrity.

#### **Timestamps**

- Converted `PURCHASE_TS` and `SHIP_TS` to datetime.
- Identified 5 missing purchase dates and a small number of missing ship dates.
- Noted some orders where ship date precedes purchase date (data entry errors).

#### **Product Names**

- Found 8 unique products, with Nintendo Switch being the most popular.
- Corrected spelling inconsistencies (e.g., "27inches 4k gaming monitor" to "27in 4K gaming monitor").

#### **Prices**

- Detected 5 missing prices and 29 orders with $0 price.
- Decided to fill those missing prices using the average of the product price around the date or purchase.
- Replaced $0 prices with the average price of the products around the purchase date.

#### **Other Columns**

- Checked for missing values in `PURCHASE_PLATFORM`, `MARKETING_CHANNEL`, `ACCOUNT_CREATION_METHOD`, and `COUNTRY_CODE`.
- Filled missing `MARKETING_CHANNEL` and `ACCOUNT_CREATION_METHOD` with 'unknown' category.

#### **Data Consistency**

- Found ~2,000 orders with ship date before purchase date, likely due to data entry mistakes.
- Calculated average negative time to ship and documented the issue.

---

### 3. Evaluate Unsolvable Issues

- Remaining issues: missing purchase dates, missing country codes, and inconsistent shipping dates.
- Decided to keep these rows due to their small magnitude and lack of external data for correction.

---

### 4. Augment the Data

- Engineered new features: purchase and ship year, month, day, weekday, and time to ship (in hours).
- Mapped country codes to regions using an external lookup table and merged region info into the dataset.

---

### 5. Final Steps

- Filtered out rows with negative time to ship for the final cleaned dataset.
- Saved the cleaned data to CSV for further analysis.

---

### Summary

The data cleaning process ensured a reliable and consistent dataset for analysis. All major issues were addressed, and remaining minor issues were documented. The dataset is now ready for exploratory data analysis (EDA).

## Exploratory Data Analysis (EDA) Report

### EDA Overview

The EDA phase explored the cleaned Game Zone dataset to uncover trends, patterns, and actionable insights. The analysis focused on sales metrics, product and regional performance, time-based trends, and marketing channels.

---

### 1. Initial Exploration

- Loaded the cleaned dataset and reviewed its structure and key columns.
- Confirmed data types and checked for any remaining missing values.

---

### 2. Sales Summary

- Created a pivot table to summarize total sales by product and month.
- Calculated overall total sales: **$5,542,945.59** from Jan 2019 to Feb 2021.
- Identified the most popular products by sales (USD): **27in 4K gaming monitor**, **Nintendo Switch**, and **Sony PlayStation 5 bundle**.
- Noted least popular products by sales: **Razer Pro Gaming Headset**, **Dell Gaming Mouse**, **Acer Nitro laptop**.

---

### 3. Sales Over Time

- Analyzed monthly sales trends, revealing a significant increase in sales from late 2019 through 2020, peaking in December 2020.
- Visualized sales by product, showing that all major products followed the overall sales trend.
- Identified January 2020 as the month with the least sales (~$86k) and December 2020 as the peak (~$500k).

---

### 4. Regional Analysis

- Grouped sales by region, finding that **Americas** and **Europe** were the strongest markets for our products.
- Observed that regional sales trends closely matched overall and product-specific trends.

---

### 5. Marketing Channel Analysis

- Explored sales by marketing channel for top products.
- Found that the **Direct** channel was dominant, with most users ordering directly from the website.
- Identified potential for growth in **Email** and **Affiliate** channels.

---

### 6. Metric Decomposition

- Broke down sales into **Order Count** and **Average Order Value (AOV)** by product and month.
- Found that order counts and AOV trends aligned with overall sales patterns.
- Noted that some products (e.g., Sony PlayStation bundle, Acer laptop) showed more price fluctuation over time.

---

### 7. Key Insights

- Sales growth was global across products and regions, especially during the COVID-19 period.
- Direct marketing is highly effective, other channels have room for improvement.
- Product pricing is generally stable, with some exceptions.
- However, the last few months show negative trends in sales.

---

### Conclusion

The EDA provided a comprehensive understanding of sales performance, product and regional trends, and marketing effectiveness. These insights set the stage for deeper analysis or modeling.
