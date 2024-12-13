# Project Overview
This project is a comprehensive analysis of pizza sales data using SQL and Power BI to understand sales performance and customer preferences. The main goal is to help the client identify top and worst-selling pizzas, determine the most profitable and popular pizza types, and make informed decisions based on sales patterns. The data covers multiple metrics such as revenue, quantity sold, and total orders over a defined date range. This project combines SQL for data querying and manipulation, and Power BI for data visualization, allowing users to easily interact with and interpret complex sales data through intuitive dashboards and visual reports.

# Features Section:
Data Extraction: SQL scripts used to extract relevant pizza sales data from various sources, ensuring all necessary information is captured for analysis.

Data Cleaning: Techniques applied to prepare and clean the dataset, handling missing values, correcting inconsistencies, and transforming data for easier analysis.

Sales Trend Analysis: Visualizations that display the overall trends in pizza sales over time, allowing users to understand seasonality and peak periods.

KPI Calculation: The project calculates key performance indicators (KPIs) such as total revenue, average order size, and order frequency to measure business performance effectively.

Product Performance Insights: Reports and visualizations that provide detailed insights into the sales performance of different pizza types, highlighting top and worst sellers.

Interactive Dashboard in Power BI: An interactive dashboard built using Power BI where users can filter and explore data, view different charts and graphs, and drill down into specific metrics.

Custom Visualizations: Custom visuals including heat maps for sales density, pie charts for order distribution, bar charts for product comparison, and trend lines to show growth patterns.

# Technologies Used:
SQL: Employed for querying and analyzing the pizza sales data. SQL scripts were used to extract, clean, and manipulate data.
Power BI: Utilized to build an interactive dashboard that visualizes sales trends, KPIs, and product performance. The dashboard includes charts, graphs, and custom visuals for detailed analysis.
## SQL
## Pizza Sales Dataset

This dataset contains sales information used for the pizza sales analysis project.
### CSV File
The dataset can be downloaded from [Google Drive](https://drive.google.com/file/d/1yPYIApqIW3L9oYdwdFU-TRVxJudUTa4D/view?usp=sharing).

# Pizza Sales Analysis-SQL Queries

This document provides SQL queries for analyzing pizza sales data.

## Table of Contents
- [KPIs](#kpis)
- [Daily and Monthly Trends](#daily-and-monthly-trends)
- [Sales Breakdown](#sales-breakdown)
- [Top and Bottom Performers](#top-and-bottom-performers)
- [How to Use](#how-to-use)

## KPIs

### 1. Total Revenue
```sql
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
```
Calculates the total revenue generated from pizza sales.

### 2. Average Order Value
```sql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;
```
Determines the average revenue per order.

### 3. Total Pizzas Sold
```sql
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;
```
Finds the total quantity of pizzas sold.

### 4. Total Orders
```sql
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;
```
Counts the total number of unique orders.

### 5. Average Pizzas Per Order
```sql
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Avg_Pizzas_per_order FROM pizza_sales;
```
Calculates the average number of pizzas per order.

## Daily and Monthly Trends

### Daily Orders
```sql
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales 
GROUP BY DATENAME(DW, order_date);
```
Shows the daily trend of total orders.

### Monthly Orders
```sql
SELECT DATENAME(MONTH, order_date) AS Month_Name, COUNT(DISTINCT order_id) AS Total_Orders 
FROM pizza_sales 
GROUP BY DATENAME(MONTH, order_date);
```
Analyzes the monthly trend for orders.

## Sales Breakdown

### % of Sales by Pizza Category
```sql
SELECT pizza_category, 
       CAST(SUM(total_price) AS DECIMAL(10,2)) AS total_revenue, 
       CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT 
FROM pizza_sales 
GROUP BY pizza_category;
```
Calculates the percentage of sales by each pizza category.

### % of Sales by Pizza Size
```sql
SELECT pizza_size, 
       CAST(SUM(total_price) AS DECIMAL(10,2)) AS total_revenue, 
       CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT 
FROM pizza_sales 
GROUP BY pizza_size 
ORDER BY pizza_size;
```
Calculates the percentage of sales by each pizza size.

## Top and Bottom Performers

### Top 5 Pizzas by Revenue
```sql
SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue 
FROM pizza_sales 
GROUP BY pizza_name 
ORDER BY Total_Revenue DESC;
```
Lists the top 5 pizzas that generated the highest revenue.

### Bottom 5 Pizzas by Revenue
```sql
SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue 
FROM pizza_sales 
GROUP BY pizza_name 
ORDER BY Total_Revenue ASC;
```
Lists the bottom 5 pizzas that generated the lowest revenue.

### Top 5 Pizzas by Quantity
```sql
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold 
FROM pizza_sales 
GROUP BY pizza_name 
ORDER BY Total_Pizza_Sold DESC;
```
Lists the top 5 pizzas based on the total quantity sold.

## How to Use

1. Ensure you have access to the `pizza_sales` database.
2. Open your SQL query editor (e.g., SQL Server Management Studio, MySQL Workbench, or pgAdmin).
3. Copy and paste any of the above queries into the editor.
4. Execute the query to view results.
5. Customize the queries as needed for further analysis.

## Using Power BI with a CSV File
1: Download and save your CSV file locally.
2: Open Power BI and go to “Home” > “Get Data” > “Text/CSV”.
3: Browse to the location where your CSV file is stored and select it.
4: Click “Load” to import the data into Power BI. This will create a new table in your Power BI model.
5: Once your data is imported, you can use Power BI to manipulate and analyze it. You can create new columns, perform calculations, and generate reports using the provided SQL queries as a guide.
6: Use the “Transform Data” option to refine and clean your imported data if necessary. This step allows you to adjust data types, handle missing values, and format the dataset for easier analysis.
## Pizza Sales Dashboard Overview

![pizza-sales1](https://github.com/user-attachments/assets/2ceff51c-d1c3-4ccb-b7f6-038a016ee76e)

![image](https://github.com/user-attachments/assets/714ba300-ecaf-408c-8367-bb038ed66faf)


















