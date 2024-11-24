# sales-insights-POWER-BI-

#### power bi project link: [sales-insights - Power BI](https://app.powerbi.com/groups/me/reports/404de9ab-0630-42e1-98a6-0ceefd35d3fd?pbi_source=desktop)

# SQL Data Cleaning and Sales Analysis Project
`
  This project showcases a complete data cleaning process using SQL queries, followed by sales insights analysis presented through a Power BI report. The dataset involves multiple tables related to customers, transactions, markets, dates, and products. The project focuses on ensuring data quality, handling duplicates, and standardizing data for accurate analysis. Advanced DAX formulas were also utilized for enhanced analysis within Power BI.
`
# Project Overview
### Project Objective:
`
  To analyze the sales and revenue performance of the business across different regions and customer segments, identify key trends and opportunities, and provide actionable recommendations to optimize performance and increase profitability.
`

#### Specifically, the project aims to:

  `1. Assess Overall Performance:` Evaluate the overall revenue, sales, and profit performance of the business.
  `2. Identify Top-Performing Regions:` Determine the top-performing regions and understand the factors contributing to their success.
  `3. Analyze Customer Segmentation:` Identify high-value customer segments and tailor strategies to maximize their contribution.
  `4. Understand Seasonal Trends:` Analyze seasonal patterns in sales and revenue to optimize operations and marketing efforts.
  `5. Provide Actionable Recommendations:` Develop specific recommendations to improve sales, revenue, and profitability.

# Key Deliverables:
  ### SQL Scripts for Data Cleaning:
      1. Creation of duplicate tables for backup and cleaning.
      2. Detection and removal of duplicate rows.
      3. Standardization of naming conventions and data formats.
      4. Data normalization and outlier removal.
   
# Power BI Report for Sales Insights:
  ### Revenue and sales performance.
    1. Geographic and customer segmentation analysis.
    2. Seasonal trends.
    3. DAX Formulas for Advanced Analysis:
    4. Calculations for profit margin, revenue contribution, and year-over-year performance.

# SQL Data Cleaning Process:
  ### Step 1: Create Duplicate Tables
    Duplicate tables (customers_duplicate, transactions_duplicate, etc.) were created to preserve the original data while performing cleaning operations.   
  ### Step 2: Handle Duplicates
    Used Common Table Expressions (CTEs) and the ROW_NUMBER() function to identify duplicate rows.
    Deleted or flagged duplicates in tables like transactions_duplicate.
  ### Step 3: Standardization
    Removed extra spaces using the TRIM() function.
    Verified naming consistency using DISTINCT queries.
  ### Step 4: Data Normalization
    Added a new column, currency_normalization, to convert sales amounts from USD to INR.
  ### Step 5: Outlier Removal
    Removed invalid or zero sales amounts from the transactions_duplicate table.
    
# Power BI Sales Insights Report
  ### DAX Formulas for Analysis
    To enhance the Power BI report, advanced DAX formulas were implemented, enabling deeper insights into sales and profitability.
    Below are key formulas used:

### 1. Profit Margin Contribution Percentage:
  `
    Profit Margin Contribution Percentage = 
    DIVIDE(
        [total_profit_margin],
        CALCULATE(
            [total_profit_margin],
            ALL('sales products_duplicate'),
            ALL('sales customers_duplicate'),
            ALL('sales markets_duplicate')
        ),
        0
    )
  `

### 2. Profit Margins:
`
profit_margins = DIVIDE([total_profit_margin], [revenue], 0)
`

### 3. Revenue:
`
revenue = SUM('sales transactions_duplicate'[currency_normalization])
`

### 4. Revenue Margin Contribution Percentage::
`
Revenue Margin Contribution Percentage = 
DIVIDE(
    [revenue],
    CALCULATE(
        [revenue],
        ALL('sales products_duplicate'),
        ALL('sales customers_duplicate'),
        ALL('sales markets_duplicate')
    ),
    0
)

### 5. Revenue Last Year:
`
revenue_last_year = CALCULATE([revenue], SAMEPERIODLASTYEAR('sales date_duplicate'[date]))
`

### 6. Sales Quantity::
`
sales_quantity = SUM('sales transactions_duplicate'[sales_qty])
`

### 7. Total Profit:
`
Total Profit = SUMX('sales transactions_duplicate', [revenue] - [cost_price])
`

### 8. Total Profit Margin:
`
total_profit_margin = SUM('sales transactions_duplicate'[profit_margin])
`

# Key Findings:
  ### 1. Strong Revenue and Sales Performance:
    `Total revenue: ₹984.84 million`
    `Total sales: 2 million units`
    
  ### 2. Geographic Performance:
    `Top-performing regions: Delhi NCR, Mumbai, Ahmedabad.
    Bangalore has the lowest sales and revenue.`
    
  ### 3. Customer Segmentation:
    `High-value customers: Electrical Stores.
    Significant contribution by brick-and-mortar customers.`
    
  ### 4. Seasonal Trends:
    `Peak quarter: Q1
    Lowest sales quarter: Q3`
