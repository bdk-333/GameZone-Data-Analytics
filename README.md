# Data Cleaning technique

## Plan for data cleaning

In this cleaning process, I'll be using the **"CLEAN"** approach.

1. **C**: Conceptualize the Data.
    - This means understant the date. What each row represents in your data or table? Which are the quantitative features and which are the qualitative features, which features is or could be the target of the analysis? Which features aren't that important in the analysis?, etc.
2. **L**: Locate Solvable Problems.
    - This is the first pass of data cleaning, here we try to find and fix the "low-hanging fruits", meaning the obvious errors that we can quickly notice and deal with.
    - It includes going through each features and checking for inconsistencies like spelling (USA vs United States vs America), data formatting (12-12-12 vs 12/12/12), leading or trailing characters or spaces (e.g., ---monitors----, "   bike ", etc.), checking for missing values, duplicate values, checking data types, etc.
3. **E**: Evaluate Unsolvable issues.
    - In this step we try to deal with the issues that are not so easy to deal with like handling missing data. In this case, we can either keep it as it is, or impute it.
        - Most probably for the analysis step we keep the data as it is and not impute it, because imputing data introduces bias which could be mislead the analysis.
        - However, we can still impute if we have a truth source, for example if the product price is missing, we can filter the price from another, say products, for the purchase data because we have recorded the product data into another table.
    - Investigate outliers. Is these rows genuine or just an entry error? In most cases we keep the outliers if they are actually genuine.
    - And for the problems that we can't solve, we flag it. Meaning that if in the data we find all the data missing from Dec, and we have no way of accessing that data, we flag it as an issue, e.g., to the stakeholder.
4. **A**: Augment the data.
    - Now that we have cleaned data, we try to make it more powerful for analysis by creating new features using the ones we already have.
    - For example, we have purchase data, from this we can create purchase year, month and day. If we have age, we can create age groups like teenagers, young adults, adults, etc. If we have country code, we can use a lookup table and create a region table, etc.
5. **N**: Note and document.
    - We keep a record of our cleaning at every step, so that others or even our future self can understand what we did and how. It builds trust in your process and transparency.
    - We note our actions ('A') and issues we find in the ('L' and 'E') steps, for example filled 50 missing values in a column with unknown, or 1000 rows are missing purchase date, kept it but didn't include it for time series analysis, etc.
    - Through the cleaning process, we keep an issue log, where we write any issues we find, it's magnitude (what percent of data is affected), ideas of how it can be solved, resolution, etc.
