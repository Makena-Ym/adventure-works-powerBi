Project Overview
This repository contains a Power BI Desktop project based on the AdventureWorks (or analogous sales) dataset. The goal is to equip decision-makers with insights on revenue trends, product performance, regional sales, and profitability through:

A streamlined ETL pipeline

Robust data cleaning

Star schema data modeling

Dynamic DAX calculations

High-impact, interactive dashboard visuals

Data Sources
Sales Transactions (CSV/Excel)

Product Catalog (CSV/Excel)

Customer Details (CSV/Excel)

Geography & Region (CSV/Excel)

Date Table (Generated in Power Query)

ETL Process
Connect to Source Files

Import CSV/Excel files via Power Query

Identify and parameterize file paths for reusability

Initial Query Setup

Name each query by business entity (e.g., Sales, Products, Customers)

Set data types consistently (dates, decimals, texts)

Merge & Append

Append monthly sales files into a single Sales table

Merge Sales with Products and Customers on matching keys

Generate Date Table

Use M code to create a contiguous date dimension

Add attributes: Year, Quarter, MonthName, Weekday

Data Cleaning & Transformation
Remove null or blank records in key columns

Trim leading/trailing spaces from text fields

Standardize date formats and locale settings

Filter out test or outlier transactions

Unpivot measures (if necessary) to normalize column structure

Create calculated columns in Power Query for flags (e.g., IsHighValueOrder)

Data Modeling
Establish a star schema:

Table	Key	Role
Sales	SalesOrderID	Fact table
Products	ProductID	Dimension table
Customers	CustomerID	Dimension table
Geography	RegionID	Dimension table
Date	DateKey	Dimension table
Define one-to-many relationships from each dimension to Sales

Enforce cross-filtering directions where appropriate

Hide raw keys and unnecessary columns for cleaner field lists

DAX Measures & KPIs
Key measures implemented:

Total Sales = SUM(Sales[SalesAmount])

Total Orders = DISTINCTCOUNT(Sales[SalesOrderID])

Profit Margin = (SUM(Sales[SalesAmount]) - SUM(Sales[TotalCost])) / SUM(Sales[SalesAmount])

Return Rate = SUM(Sales[ReturnedQuantity]) / SUM(Sales[OrderQuantity])

Sales YTD = TOTALYTD([Total Sales], 'Date'[Date])

Visualizations
Visual Type	Description	Page Location
Clustered Column	Sales by Product Category	Overview
Line Chart	Monthly Revenue Trend	Trends
Map (Filled)	Regional Sales Distribution	Geo Analysis
Matrix	Top 10 Customers by Sales and Profit Margin	Customers
Card	High-level KPIs (Total Sales, Profit Margin)	Header
Slicer Panel	Year, Quarter, Product Category, Region	Persistent Filter
Interactive features:

Drillthrough to see order-level details

Bookmarks for snapshot comparison (e.g., pre vs. post-promotion)

Custom tooltips showing product images and margin breakdown

Report Layout
Cover Page

Title, date filter, overall KPIs

Overview Page

Sales by category, region, trend snapshot

Trends Page

Detailed time series and YoY analysis

Geo Analysis

Map visuals with heatmap styling

Customer Analysis

Matrix and bar chart of top customers

Order Details (Drillthrough)

Transaction-level table with search and export

Tools & Technologies
Power BI Desktop

Power Query (M language)

DAX (Data Analysis Expressions)

Git & GitHub for version control

Microsoft Excel (for initial raw data files)

Author & License
Author: Makena Gatere: your.makenamugambi8@gmail.com

This project is licensed under the MIT License. Feel free to fork, adapt, and contribute back.
