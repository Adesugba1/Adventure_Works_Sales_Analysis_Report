# Adventure Sales Analysis

## Table of Content
- [Overview](#overview)
- [Data Source](#data-source)
- [Tools Used](#tools-used)
- [Data Preparation and Cleaning](#data-preparation-and-cleaing)
- [Data Modeling](#data-modeling)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [DAX Calculations and Measures](#dax-calculations-and-measures)
- [Key Findings and Insights](#key-findings-and-insights)
- [Strategic Recommendations](#strategic-recommendations)
- [Conclusion](#concluson)

## Overview
This report presents a comprehensive analysis of Adventure Works' sales performance based on the transformed dataset. Key performance indicators (KPIs) analyzed include total revenue, cost of goods sold (COGS), total profit, profit margins, and transactional insights. The analysis spans multiple years, providing insights into revenue trends, profit contributions, and regional performance.

## Data Source
The primary datadet use for this analysis contains six different tables; 
FactInternetSales (26 Columns, 60,398 Rows), 
DimCustomers (29 Columns, 18,484 rows), 
DimDate (19 Columns, 2,191 rows), 
DimSalesTerritory (6 Columns, 12 Rows), 
DimProduct (36 Columns, 606 Rows), 
DimGeography (11 Columns, 655 rows). 
[Download Dataset Here](https:www.x.com)

## Tools Used
- Power Query - Data Cleaning
- Microsoft Excel - Modelling, Analysis and Creating Report

## Data Preparation and Cleaning
### Data Importation
-  Each table was loaded one by one through the Data tab in Excel into Power Query for cleaning and transformation.
-  The FactSales table, which contained 26 columns and 60,398 rows, was filtered to use only 6 relevant columns for analysis.

### Data Cleaning in Power Query
#### Data Types Validation:
- All data types were checked using the "Detect Data Type" command under the "Transform" tab in Power Query.
#### Handling Missing and Irrelevant Data:
- In DimSalesTerritory, rows containing NA were removed as they affected the entire row.
- The SalesTerritoryImage column, which contained mostly NULL values, was removed.
- In DimProduct, only the relevant columns ProductKey, EnglishProductName, and Colour were selected. The NA values in the Colour column were replaced with "Unspecified".
- In DimGeography, only GeographyKey, City, and EnglishCountryRegionName were retained.
- The DimDate table was optimized by keeping only the Date column, from which Year (2005-2008), Month, Name of Month, Day Name, Week Type, and Quarter of Year were extracted for analysis.
- In DimCustomers, the columns FirstName, LastName, CustomerKey, GeographyKey, CustomerAlternateKey, BirthDate, and Gender were selected. The FirstName and LastName were merged using the "Merge" command in Power Query.

### Data Loading
•	All tables were loaded into Excel as Connections and Model from Power Query, enabling efficient data integration.

## Data Modeling
- Power Pivot in Excel was used for modeling.
- One-to-Many Relationships were created in the "Diagram View", linking tables using the following primary keys: 
  - FactSales → DimCustomers (CustomerKey)
  - FactSales → DimProduct (ProductKey)
  - FactSales → DimSalesTerritory (SalesTerritoryKey)
  - FactSales → DimGeography (GeographyKey)
  - FactSales → DimDate (DateKey)

## Exploratory Data Analysis
EDA includes exploring the dataset to answer business questions such as:
- What is the total revenue
- What is the total cost of goods sold
- Calculate the total profit across three years
- Calculate the total number of Products
- Calculate the unsold product
- Determine the region with the highest sales

## DAX Calculations and Measures
- The following key measures were created using DAX (Data Analysis Expressions) in Power Pivot: 
  - Revenue = SUM(FactSales[SalesAmount])
  - Cost of Goods Sold (COGS) = SUM(FactSales[TotalProductCost])
  - Profit = SUM(FactSales[SalesAmount]) - SUM(FactSales[TotalProductCost])
  - No. of Transactions = COUNT(FactSales[SalesOrderNumber])
  - All Products = DISTINCTCOUNT(DimProduct[ProductKey])
  - Sold Products = CALCULATE(DISTINCTCOUNT(DimProduct[ProductKey]), FactSales[SalesAmount] > 0)
  - Unsold Products = All Products - Sold Products
  - % Profit Margin = (Profit / Revenue) * 100
- Additional calculations for Total Revenue, COGS, and Order Quantity were performed using Pivot Tables.

## Key Findings and Insights
### Overall Sales Performance
- Total Revenue: $307.09 million
- Total Profit: $126.29 million
- Total COGS: $180.80 million
- Profit Margin: 41.1%
- The 41.1% profit margin reflects strong cost management and pricing efficiency.
### Transaction and Quantity Insights
- Total Transactions: 60.4K
- Total Quantity Sold: 448
Despite a high transaction count, the total quantity sold is low, suggesting that high-value products drive revenue rather than bulk sales.
### Revenue Distribution Over Time
- 66.5% of revenue was generated between 2005 and 2008.
- Revenue peaked in 2008 at $102 million, while 2005 recorded the lowest revenue at $69 million.
This indicates consistent business growth over the years.
### Profitability by Time Period
- May, June, and December contributed 31.9% of total profit.
- 72% of total profit was generated on weekdays, with Wednesdays and Thursdays being the most profitable.
Weekday sales play a crucial role, indicating a strong business demand during weekdays.
### Quarterly Profit Breakdown
- Q2 (April - June) generated the highest profit ($39.02M, 31%).
- Q3 (July - September) was the least profitable ($24.19M, 19%).
Peak profitability in Q2 aligns with strong sales in May and June.
### Regional Performance
- The key markets include United States, Canada, Australia, Germany, France, and the UK.
- The U.S. and Canada contribute significantly due to their large consumer base and higher purchasing power.

## Strategic Recommendations
### Optimize Seasonal and Weekly Strategies
- Increase targeted marketing and inventory planning during May, June, and December.
- Introduce weekday promotional offers to boost midweek sales further.
### Diversify Revenue Streams
- Since transactions are high but quantity sold is low, introducing lower-cost, high-volume products could attract price-sensitive customers.
### Strengthen Q3 Sales Performance
- Q3 (July - September) is the weakest quarter.
- Implement discounts, promotions, or new product launches to boost revenue.
### Expand Geographic Focus
- The U.S. and Australia should be the primary focus for growth.
- Increased localized marketing in Germany and the UK can improve European market penetration.
### Improve Customer Retention Strategies
- Since 66.5% of revenue comes from repeat customers, strengthening loyalty programs, personalized offers, and engagement strategies is crucial.

## Conclusion
Adventure Works exhibits strong revenue growth, high profit margins, and clear seasonal profitability trends. However, there are opportunities for further optimization in quarterly performance, sales volume, and customer retention. Implementing the proposed strategies will maximize profitability, reduce revenue volatility, and sustain business growth.

