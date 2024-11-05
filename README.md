# LITA_PROJECT

### Project Title: sales Performance Analysis for a Retail Store and Customer Segmentation for a Subscription Service

[Project Overview](#Project-Overview)

[Data Sources](#Data-Sources)

[Tools Used](#Tools-Used)

[Microsoft Excel](#MicrosoftExcel)

[SQL Analysis](#SQL-Analysis)

[Microsoft PowerBi](#Microsoft-PowerBi)

[Data visualization](#Data-visualization)

[Conclusion](#Conclusion)


---
### Project Overview
The first project aims to analyze and visualize the sales performance of a retail store by exploring and uncovering key insights in the sales data. We’ll use Excel for initial exploration, SQL to answer business questions, and Power BI to create an interactive dashboard that presents our findings. The analysis will cover top-selling products, regional performance, monthly sales trends, and other key performance metrics.
The second project,customer data for a subscription service to identify segments, patterns, and key trends in customer behaviour. By exploring data related to subscription types, cancellations, and renewals, we aim to develop actionable insights that help improve retention and inform marketing strategies. The final deliverable will be an interactive Power BI dashboard that visualizes customer segmentation and subscription trends.

---
### Data Sources
The primary source of Data used in this project Capstone project.xlx and this is open source data that is freely downloaded from an source such as Canvas LMS

---
### Tools Used
This project utilizes the following tools and technologies for data analysis and visualization:
- Microsoft Excel: For initial data exploration, pivot tables, and calculations (e.g., average subscription duration, subscription patterns).
- SQL Server: For data storage, querying, and extraction of key insights through SQL queries.
- Power BI: For creating interactive dashboards to visualize customer segments, cancellations, and subscription trends.
- Github for Portfolio Building

---
### Project one: Sales Performance Analysis for a Retail Store
 #### Microsoft Excel
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

---
  #### Data visualization
  ##### Pivot Tables
![pivot table 1](https://github.com/user-attachments/assets/15453052-120f-40c7-869b-0cc555c7447b)

![pivot table 2](https://github.com/user-attachments/assets/eda42d7f-7219-4141-a75a-9135bf9eece6)

##### Charts
![image](https://github.com/user-attachments/assets/546215eb-5f8c-4ba3-a981-ab93c8007213)

![image](https://github.com/user-attachments/assets/026d3835-b5cd-4f42-a558-7d64a2692b33)

![image](https://github.com/user-attachments/assets/4c9c2f65-66e8-4f09-a72f-936b3d93978e)

![image](https://github.com/user-attachments/assets/2f5f9820-e8b1-4d23-8542-1672c1fe81bb)

![image](https://github.com/user-attachments/assets/8d73da8e-cd09-414a-9b57-10d4e1941c6d)

---
### SQL Analysis
 Import the sales dataset  SQL Server environment and write SQL queries to answer specific business questions. This step provides a deeper understanding of the data and reveals additional insights.
- Queries to Complete
Total Sales by Product Category: Retrieve the total sales for each product category to identify high-performing categories.

```SQL
create database lita_salesdata

use lita_salesdata

select*from[dbo].[salesdata]

#### Question 1 Retrieve the total sales of each product by category....

SELECT 
    Product, 
    SUM([Sales_amount]) AS TotalSales 
FROM 
    SalesData 
GROUP BY 
    Product 
ORDER BY 
    TotalSales DESC;

select * from Salesdata

#### Question 2 Find the number of sales transaction in each region

SELECT 
    Region, 
    COUNT(OrderID) AS Number_of_Sales_Transactions 
FROM 
    Salesdata 
GROUP BY 
    Region 
ORDER BY 
    Number_of_Sales_Transactions DESC;

 #### Question 3 Find the highest-selling product by total sales value

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

#### Question 4 Calculate total revenue per product

SELECT
Product,
SUM(Sales_amount) AS Total_Revenue
FROM
SalesData
GROUP BY
Product
ORDER BY
Total_Revenue DESC;

##### Qusetion 5 Calculate monthly sales totals for the current year

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

SELECT TOP 5
Customer_ID,
SUM(Sales_amount) AS Total_Purchase_Amount
FROM
SalesData
GROUP BY
Customer_ID
ORDER BY
Total_Purchase_Amount DESC;

#### Question 7 Calculate the percentage of total sales contributed by each region

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

#### Question 8 Identify products with no sales in the last quarter

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
```

---
#### Data visualization

![Sql sales data](https://github.com/user-attachments/assets/d58fa77d-3486-4286-b7f5-ddcec6ee3139)

![Sql sales data1](https://github.com/user-attachments/assets/5cc77193-417a-4d39-8877-7c68f8611d96)

![Sql sales data2](https://github.com/user-attachments/assets/e47a785c-cf41-4903-b39c-13162a3fb761)

![Sql sales data3](https://github.com/user-attachments/assets/2749602e-b969-474d-83ae-92934e113561)

---
### Microsoft PowerBi
Build an interactive Power BI dashboard to visualize the results. Key components should include:
#### Sales Overview:
- Overall sales performance summary, including total revenue and sales trends over time.
- Top-Performing Products:
- Display the highest-selling products with detailed breakdowns.
- Regional Sales Breakdown:
- Show performance by region, with filters for detailed analysis.

---
#### Data visualization

![Powerbi sales data](https://github.com/user-attachments/assets/de43486b-a6ce-4a21-954c-ca39966314af)

![sales data regional map](https://github.com/user-attachments/assets/86485c6b-34f3-47f4-9ac9-3c5930ea4fd6)

![sales data slicers](https://github.com/user-attachments/assets/3422d595-d4a1-4421-a6e0-25807afce654)

---
### Project two: Customer Segmentation for a Subscription Service

---
#### Microsoft Excel
- Data Exploration:
- Use pivot tables to analyze subscription patterns by region and subscription type.
- Metrics Calculation: Calculate the average subscription duration and determine the most popular subscription types.

---
#### Data visualization
##### Pivot table
![Pivot table customer data](https://github.com/user-attachments/assets/9820aed4-3f5b-48ab-89e1-c30834fdd27f)

##### Charts

![image](https://github.com/user-attachments/assets/df982f3f-2d64-4c7f-bee5-d8b3b3eb1c99)

![image](https://github.com/user-attachments/assets/d7fc5386-4556-480e-9a37-76ec7cab6729)

---
### SQL Analysis
Load the dataset into an SQL Server environment to extract insights through SQL queries. Focus on answering the following questions:

- Customer Regions:
   - Retrieve the total number of customers from each region.
- Popular Subscription Types:
   - Find the most popular subscription type by customer count.
Cancellations:
   - Identify customers who canceled within 6 months of subscribing.
Subscription Duration:
   - Calculate the average subscription duration for all customers.
   - Identify customers with subscriptions longer than 12 months.
- Revenue by Subscription:
   - Calculate total revenue generated by each subscription type.
- Top Regions by Cancellations:
   - Find the top 3 regions with the highest cancellation rates.
- Subscription Status:
   - Determine the total number of active and canceled subscriptions.

```SQL
create database lita_customerdata

use lita_customerdata

select*from[dbo].[customerdata]

....Question 1 Retrieve the total number of customers from each region....

SELECT  Region, 
 COUNT(CustomerID) AS TotalCustomers
FROM 
  CustomerData
GROUP BY 
  Region
ORDER BY 
  TotalCustomers DESC;

  select * from [dbo].[customerdata]

 ..... Question 2 Find the most popular subscription type by the number of customers......

SELECT
SubscriptionType,
COUNT(CustomerID) AS TotalCustomers
FROM
CustomerData
GROUP BY
SubscriptionType
ORDER BY
TotalCustomers DESC;

......Question 3 Find customers who canceled their subscription within 6 months......

SELECT
CustomerID,
CustomerName,
SubscriptionType,
SubscriptionStart,
SubscriptionEnd,
DATEDIFF(month, SubscriptionStart, SubscriptionEnd) AS SubscriptionDuration
FROM
CustomerData
WHERE
Canceled = 1
AND DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6
ORDER BY
SubscriptionDuration ASC;

....Question 4 Calculate the average subscription duration for all customers......

SELECT 
  AVG(DATEDIFF(month, SubscriptionStart, SubscriptionEnd)) AS AverageSubscriptionDuration
FROM 
  Customerdata
WHERE 
  Canceled = 1;

  select * from [dbo].[customerdata]

 ...... Qustion 5 Find customers with subscriptions longer than 12 months.......

  SELECT 
  CustomerID,
CustomerName,
SubscriptionType,
SubscriptionStart,
SubscriptionEnd,
DATEDIFF(month, SubscriptionStart, SubscriptionEnd) AS SubscriptionDuration
FROM
CustomerData
WHERE
DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12
ORDER BY
SubscriptionDuration DESC;

......Question 6 Calculate total revenue by subscription type.......

SELECT SubscriptionType,
SUM(Revenue) AS TotalRevenue
FROM
CustomerData
GROUP BY
SubscriptionType
ORDER BY
TotalRevenue DESC;

.......Question 7 Find top 3 categories by subscription cancellations.......

SELECT TOP 3
SubscriptionType,
COUNT(CustomerID) AS CancellationCount
FROM
CustomerData
WHERE
Canceled = 1
GROUP BY
SubscriptionType
ORDER BY
CancellationCount DESC;

select * from [dbo].[customerdata]

........Question 8 Find the total number of active and canceled subscription......

SELECT SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM
CustomerData;
```
----
##### Data visualization

![Sql customer data](https://github.com/user-attachments/assets/1268692b-170c-4df4-b615-820b44ec44d8)

![Sql customer data1](https://github.com/user-attachments/assets/a83346a7-de00-4105-a3d3-8a38f9c8e3cf)

![Sql customer data2](https://github.com/user-attachments/assets/81f421ce-b70d-46d3-b37d-8b14e7a11539)

![Sql customer data3](https://github.com/user-attachments/assets/d8c85743-9cff-4bd2-8dad-6b428fcd44f1)

---
### Microsoft PowerBi
Create an interactive Power BI dashboard that visualizes the insights from Excel and SQL, with the following element
- Customer Segmentation:
   - Visualize customer distribution by region and subscription type.
- Subscription Trends:
   - Track active vs. canceled subscriptions over time and by region.
- Cancellations and Renewals:
   - Highlight trends in cancellations and identify factors influencing them.
- Interactive Slicers:
   - Include slicers for segmenting data by subscription type, region, and customer duration.

---
##### Data visualization

![Powerbi customer data](https://github.com/user-attachments/assets/0dfa2179-146b-4688-b35a-74cd8c55ce12)

![Powerbi customer data1](https://github.com/user-attachments/assets/92d89a92-4e0e-4b0f-aaa5-993bede95e1f)

![Powerbi customer data2](https://github.com/user-attachments/assets/01d81e60-262b-4cd8-a2a7-0145fd9db878)

---
### Conclusion
1. The Sales Performance Analysis for a Retail Store project enabled a comprehensive examination of the store’s sales data, revealing key insights into top-selling products, regional sales performance, and monthly sales trends. By leveraging Excel for data exploration and metric calculations, SQL for querying specific sales insights, and Power BI for creating an interactive dashboard, we were able to uncover actionable insights.
2. The interactive Power BI dashboard provides a clear overview of sales performance, highlighting top products and key regions while enabling stakeholders to drill down into monthly and regional trends. This analysis equips the retail team with data-driven insights to optimize inventory, tailor marketing efforts by region, and focus on high-performing products to drive growth.
Overall, this project demonstrates the value of a structured approach to data analysis. It combines multiple tools to transform raw data into strategic insights that support more informed decision-making and promote stronger sales performance.

3. The Customer Segmentation for a Subscription Service project provided valuable insights into customer behaviours, subscription patterns, and trends in cancellations and renewals. By leveraging Excel, SQL, and Power BI, we identified key customer segments and the most popular subscription types, calculated average subscription durations, and highlighted regional differences in subscription trends.
The Power BI dashboard enables stakeholders to interactively explore and monitor subscription metrics, helping them make data-driven decisions to improve customer retention, tailor subscription offerings, and target marketing efforts effectively. Insights gained from this analysis can guide strategic initiatives to enhance customer engagement and optimize revenue growth.
This project demonstrates the power of data analysis and visualization in understanding customer segments, optimizing services, and ultimately supporting a more customer-centric business model.

