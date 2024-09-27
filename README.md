# Sales Insights Data Analysis Project

This project involves analyzing sales data using MySQL for querying the dataset and Power BI for creating visual insights. Below are the steps and queries used to extract valuable insights from the data.

## Prerequisites

- MySQL installed on your local machine.
- Power BI Desktop installed for data visualization.
- A basic understanding of SQL queries.

## Getting Started

### Step 1: Database Setup

1. Download the `db_dump.sql` file from this re

Step 2: Data Analysis Using SQL
1.Show all customer records:
SELECT * FROM customers;
2.Show the total number of customers:
SELECT COUNT(*) FROM customers;
3.Show transactions for the Chennai market (market code for Chennai is Mark001):
SELECT * FROM transactions WHERE market_code='Mark001';
4.Show distinct product codes sold in Chennai:
SELECT DISTINCT product_code FROM transactions WHERE market_code='Mark001';
5.Show transactions where currency is US Dollars (USD):
SELECT * FROM transactions WHERE currency="USD";
6.Show transactions for the year 2020 (joined by the date table):
SELECT transactions.*, date.* 
FROM transactions 
INNER JOIN date 
ON transactions.order_date = date.date 
WHERE date.year = 2020;
7.Show total revenue for the year 2020:
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date 
ON transactions.order_date = date.date 
WHERE date.year = 2020 
AND (transactions.currency="INR" OR transactions.currency="USD");
8.Show total revenue for January 2020:
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date 
ON transactions.order_date = date.date 
WHERE date.year = 2020 
AND date.month_name = "January" 
AND (transactions.currency="INR" OR transactions.currency="USD");
9.Show total revenue for 2020 in the Chennai market:
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date 
ON transactions.order_date = date.date 
WHERE date.year = 2020 
AND transactions.market_code = "Mark001";


Step 3: Data Analysis Using Power BI
After performing the SQL queries, the data is loaded into Power BI for further analysis and visualization.

1. Formula to create norm_amount column:
This formula normalizes the sales amount to INR if the currency is USD.
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] = "USD#(cr)" then [sales_amount] * 75 else [sales_amount], type any)

2.
Here’s how you can structure your README file for your GitHub repository based on your Sales Analysis Project:

markdown
Copy code
# Sales Insights Data Analysis Project

This project involves analyzing sales data using MySQL for querying the dataset and Power BI for creating visual insights. Below are the steps and queries used to extract valuable insights from the data.

## Prerequisites

- MySQL installed on your local machine.
- Power BI Desktop installed for data visualization.
- A basic understanding of SQL queries.

## Getting Started

### Step 1: Database Setup

1. Download the `db_dump.sql` file from this repository to your local machine.
2. Import the SQL dump into your MySQL database using the following command:
   ```bash
   mysql -u your_username -p your_database < db_dump.sql
Ensure the data has been imported successfully by checking the tables in your database.
Step 2: Data Analysis Using SQL
Here are the SQL queries used to analyze the sales data:

Show all customer records:

sql
Copy code
SELECT * FROM customers;
Show the total number of customers:

sql
Copy code
SELECT COUNT(*) FROM customers;
Show transactions for the Chennai market (market code for Chennai is Mark001):

sql
Copy code
SELECT * FROM transactions WHERE market_code='Mark001';
Show distinct product codes sold in Chennai:

sql
Copy code
SELECT DISTINCT product_code FROM transactions WHERE market_code='Mark001';
Show transactions where currency is US Dollars (USD):

sql
Copy code
SELECT * FROM transactions WHERE currency="USD";
Show transactions for the year 2020 (joined by the date table):

sql
Copy code
SELECT transactions.*, date.* 
FROM transactions 
INNER JOIN date 
ON transactions.order_date = date.date 
WHERE date.year = 2020;
Show total revenue for the year 2020:

sql
Copy code
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date 
ON transactions.order_date = date.date 
WHERE date.year = 2020 
AND (transactions.currency="INR" OR transactions.currency="USD");
Show total revenue for January 2020:

sql
Copy code
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date 
ON transactions.order_date = date.date 
WHERE date.year = 2020 
AND date.month_name = "January" 
AND (transactions.currency="INR" OR transactions.currency="USD");
Show total revenue for 2020 in the Chennai market:

sql
Copy code
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date 
ON transactions.order_date = date.date 
WHERE date.year = 2020 
AND transactions.market_code = "Mark001";
Step 3: Data Analysis Using Power BI
After performing the SQL queries, the data is loaded into Power BI for further analysis and visualization.

1. Formula to create norm_amount column:
This formula normalizes the sales amount to INR if the currency is USD.

m
Copy code
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] = "USD#(cr)" then [sales_amount] * 75 else [sales_amount], type any)
2. Data Visualization
-Visualize insights such as:
-Total sales by year.
-Market-wise sales distribution.
-Monthly sales performance.
-Use slicers to filter data by currency, market, and year

Project Structure
-db_dump.sql: The MySQL database dump file containing the sales data.
-README.md: This README file with project details.

Tools Used
MySQL: For querying and data extraction.
Power BI: For creating interactive visualizations and dashboards.
