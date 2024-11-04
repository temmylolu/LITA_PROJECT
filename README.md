# LITA_PROJECT

### Project Title: sales Performance Analysis for a Retail Store and Customer Segmentation for a Subscription Service

### Project Overview
The first project aims to analyze and visualize the sales performance of a retail store by exploring and uncovering key insights in the sales data. We’ll use Excel for initial exploration, SQL to answer business questions, and Power BI to create an interactive dashboard that presents our findings. The analysis will cover top-selling products, regional performance, monthly sales trends, and other key performance metrics.

The second project,customer data for a subscription service to identify segments, patterns, and key trends in customer behaviour. By exploring data related to subscription types, cancellations, and renewals, we aim to develop actionable insights that help improve retention and inform marketing strategies. The final deliverable will be an interactive Power BI dashboard that visualizes customer segmentation and subscription trends.

### Data Sources
The primary source of Data used in this project Capstone project.xlx and this is open source data that is freely downloaded from an source such as Canvas LMS

### Tools Used
This project utilizes the following tools and technologies for data analysis and visualization:
- Microsoft Excel: For initial data exploration, pivot tables, and calculations (e.g., average subscription duration, subscription patterns).
- SQL Server: For data storage, querying, and extraction of key insights through SQL queries.
- Power BI: For creating interactive dashboards to visualize customer segments, cancellations, and subscription trends.
- Github for Portfolio Building

 ### Microsoft Excel

#### Project one: sales Performance Analysis for a Retail Store
The first step is to load the sales data into Excel and perform an initial exploration using pivot tables and formulas.
#### Tasks
##### Summarize Total Sales:
- Use pivot tables to calculate total sales by:
-  Product
-  Region
-  Month
##### Calculate Key Metrics:
- Use Excel formulas to calculate:
- Average Sales per Product (using AVERAGEIF)
- Total Revenue by Region (using SUMIF)
- Create Additional Reports:

##### Explore other interesting metrics that can provide more insights, such as:
- Monthly sales growth
- Top-selling products over time
- Seasonal sales patterns

  #### Data Visualization
  ##### Pivot Tables
![pivot table 1](https://github.com/user-attachments/assets/15453052-120f-40c7-869b-0cc555c7447b)

![pivot table 2](https://github.com/user-attachments/assets/eda42d7f-7219-4141-a75a-9135bf9eece6)

##### Charts
![image](https://github.com/user-attachments/assets/546215eb-5f8c-4ba3-a981-ab93c8007213)

![image](https://github.com/user-attachments/assets/026d3835-b5cd-4f42-a558-7d64a2692b33)

![image](https://github.com/user-attachments/assets/4c9c2f65-66e8-4f09-a72f-936b3d93978e)

![image](https://github.com/user-attachments/assets/2f5f9820-e8b1-4d23-8542-1672c1fe81bb)

![image](https://github.com/user-attachments/assets/8d73da8e-cd09-414a-9b57-10d4e1941c6d)

### SQL Analysis
 Import the sales dataset  SQL Server environment and write SQL queries to answer specific business questions. This step provides a deeper understanding of the data and reveals additional insights.
- Queries to Complete
Total Sales by Product Category: Retrieve the total sales for each product category to identify high-performing categories.

--- SQL
create database lita_salesdata

use lita_salesdata

select*from[dbo].[salesdata]
---
#### Question 1 Retrieve the total sales of each product by category....
---
SELECT 
    Product, 
    SUM([Sales_amount]) AS TotalSales 
FROM 
    SalesData 
GROUP BY 
    Product 
ORDER BY 
    TotalSales DESC;
---
select * from Salesdata
---
#### Question 2 Find the number of sales transaction in each region
---
SELECT 
    Region, 
    COUNT(OrderID) AS Number_of_Sales_Transactions 
FROM 
    Salesdata 
GROUP BY 
    Region 
ORDER BY 
    Number_of_Sales_Transactions DESC;
---
 #### Question 3 Find the highest-selling product by total sales value
---
 SELECT TOP 1
Product,
SUM(Sales_amount) AS Total_Sales_Value
FROM
SalesData
GROUP BY
Product
ORDER BY
Total_Sales_Value DESC;

select * from [dbo].[salesdata]
---
#### Question 4 Calculate total revenue per product
---
SELECT
Product,
SUM(Sales_amount) AS Total_Revenue
FROM
SalesData
GROUP BY
Product
ORDER BY
Total_Revenue DESC;
---
##### Qusetion 5 Calculate monthly sales totals for the current year
---
SELECT
MONTH(OrderDate) AS Sales_Month,
SUM(Sales_amount) AS Monthly_Sales_Total
FROM
SalesData
WHERE
YEAR(OrderDate) = YEAR(GETDATE())
GROUP BY
MONTH(OrderDate)
ORDER BY
Sales_Month;
---
#### Question 6 Find the top 5 customers by total purchase amount
---
SELECT TOP 5
Customer_ID,
SUM(Sales_amount) AS Total_Purchase_Amount
FROM
SalesData
GROUP BY
Customer_ID
ORDER BY
Total_Purchase_Amount DESC;
---
#### Question 7 Calculate the percentage of total sales contributed by each region
---
SELECT Region, 
SUM(Sales_amount) AS Regional_Sales, 
CONVERT(DECIMAL(5,2), ROUND((CAST(SUM(Sales_amount) AS DECIMAL(10, 2)) / (SELECT SUM(Sales_amount)
FROM SalesData)) * 100, 2)) AS Sales_Percentage
FROM 
SalesData
GROUP BY 
Region
ORDER BY 
Regional_Sales DESC

select * from [dbo].[salesdata]
---
#### Question 8 Identify products with no sales in the last quarter
---
SELECT 
  Product
FROM 
  SalesData
WHERE 
  Product NOT IN (
    SELECT 
      Product
    FROM 
      SalesData
    WHERE 
      OrderDate >= DATEADD(quarter, -1, GETDATE())
  )
  AND OrderDate >= DATEADD(quarter, -1, GETDATE())
---

