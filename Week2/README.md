# SQL Customer & Order Analysis

## Project Overview

This project was completed as part of my **Week 2 Data Analytics Internship assignment at SkillNexis**.

The project focuses on analyzing customer purchase behavior and sales performance using SQL. A sample sales dataset was queried to identify high-value customers, calculate average order value, summarize customer-level sales, and generate business insights that can support customer-retention and sales strategies.

The analysis demonstrates the use of SQL queries to transform raw sales data into meaningful business information.

## Project Objectives

The main objective of this project was to analyze customer order data and answer the following business questions:

1. Who are the top customers based on total spending?
2. What is the average order value?
3. How many unique orders has each customer placed?
4. Which customers contribute the highest revenue?
5. Which customers have spending above the average customer spending?
6. What customer purchasing insights can support sales and retention decisions?

## Tools Used

- SQL
- MySQL
- MySQL Workbench
- Microsoft Excel / Google Sheets for viewing the source dataset
- GitHub for project documentation and version control

## Dataset Description

The project uses a sample sales dataset containing customer, product, order, and regional sales information.

### Sales Table

| Column Name | Description |
|---|---|
| `order_id` | Unique identifier for each customer order |
| `customer_name` | Name of the customer |
| `order_date` | Date on which the order was placed |
| `category` | Product category |
| `sub_category` | Product sub-category |
| `product_name` | Name of the product |
| `quantity` | Quantity of products ordered |
| `unit_price` | Price per unit of the product |
| `total_price` | Total transaction value, calculated as `unit_price × quantity` |
| `region` | Customer or sales region |

> Note: One `order_id` may appear across multiple rows if a customer purchased more than one product in the same order. Therefore, `COUNT(DISTINCT order_id)` is used where unique order counts are required.

## SQL Queries

### 1. Top Customers by Total Spending

This query identifies the top 10 customers based on their total purchase amount.

```sql
SELECT
    customer_name,
    COUNT(DISTINCT order_id) AS total_orders,
    ROUND(SUM(total_price), 2) AS total_spent
FROM sales
GROUP BY customer_name
ORDER BY total_spent DESC
LIMIT 10;
```

**Business Use:** Helps identify high-value customers who contribute the most revenue and may be suitable for loyalty programs, personalized offers, or retention campaigns.

### 2. Average Order Value

This query calculates the average order value across all unique orders.

```sql
SELECT
    ROUND(AVG(order_total), 2) AS average_order_value
FROM (
    SELECT
        order_id,
        SUM(total_price) AS order_total
    FROM sales
    GROUP BY order_id
) AS order_summary;
```

**Business Use:** Average order value helps measure how much customers spend per order and can be used to evaluate upselling or cross-selling opportunities.

### 3. Customer-Wise Order Summary

This query provides a customer-level summary of total orders, total sales, and average order value.

```sql
SELECT
    customer_name,
    COUNT(DISTINCT order_id) AS
average_order_value
FROM sales
GROUP BY customer_name
ORDER BY total_sales DESC;
```

**Business Use:** Provides a complete overview of each customer’s contribution to the business and purchasing behavior.

### 4. Customers With Above-Average Spending

This query identifies customers whose total spending is greater than the average spending across all customers.

```sql
SELECT
    customer_name,
    ROUND(SUM(total_price), 2) AS total_spent
FROM sales
GROUP BY customer_name
HAVING SUM(total_price) > (
    SELECT AVG(customer_total)
    FROM (
        SELECT
            customer_name,
            SUM(total_price) AS customer_total
        FROM sales
        GROUP BY customer_name
    ) AS customer_spending
)
ORDER BY total_spent DESC;
```

**Business Use:** Helps identify customers who spend more than the typical customer and may be valuable targets for retention initiatives.

## Key SQL Concepts Used

- `SELECT` for retrieving data from the sales table
- `COUNT(DISTINCT order_id)` for counting unique customer orders
- `SUM()` for calculating total revenue and customer spending
- `AVG()` for calculating average customer or order values
- `GROUP BY` for creating customer-level and order-level summaries
- `ORDER BY` for ranking customers by sales performance
- `HAVING` for filtering aggregated results
- Subqueries for comparing customer spending with the overall average
- `ROUND()` for formatting monetary values
- Aliases using `AS` for readable query output



## Project Structure

```text
SQL-Customer-Order-Analysis/
│
├── README.md
├── Customer_and_order_analysis_report.docx
├── SQL_Sales_Dataset_200_Rows.xlsx
└── screenshots/
    ├── top_customers_by_total_spending_query.png
    ├── top_customers_by_total_spending_output.png
    ├── average_order_value_query.png
    ├── average_order_value_output.png
    ├── customer_order_summary_query.png
    ├── customer_wise_order_summary_output.png
    ├── customers_with_above_average_spending_query.png
    └── customers_with_above_average_spending_output.png
```

## How to Run the Project

1. Clone or download this repository.

```bash
git clone [https://github.com/MSDIAN124/Skillnexis-Internship-Projects.git]
```

2. Open MySQL Workbench or another SQL database tool.

3. Create a database.

```sql
CREATE DATABASE sales_analysis;
USE sales_analysis;
```

4. Create the `sales` table by running the `database_schema.sql` file.

5. Import the sample sales data into the `sales` table.

6. Open and run the SQL queries available in the `sql_queries.sql` file.

7. Review the result sets to identify top customers, average order value, total orders, and customer spending patterns.

## Screenshots

🟠Top Customers by Total Spending

    
💎 QUERY :-


<img width="452" height="204" alt="Top Customers by Total Spending Query" src="https://github.com/user-attachments/assets/a29c4c24-b144-4c5f-9718-b8ba68f930f7" />


💎 OUTPUT:-

<img width="452" height="174" alt="Top Customers by Total Spending Output" src="https://github.com/user-attachments/assets/9f7bc891-4b1a-41e9-b306-9215b11d4b78" />


🟠Average Order Value


💎 QUERY:-

 
<img width="452" height="96" alt="Average Order Value Query" src="https://github.com/user-attachments/assets/3025d3d2-d34b-425e-82d2-61786374340e" />



💎 OUTPUT:-


<img width="455" height="87" alt="Average Order Value Output" src="https://github.com/user-attachments/assets/bc4ace6a-e122-490e-ba27-1c385d1c4479" />



🟠 Customer-wise Order Summary



💎 QUERY:-


<img width="452" height="188" alt="Customer-wise Order Summary Query" src="https://github.com/user-attachments/assets/30660b74-5022-48f4-b836-8735cb45fef1" />



💎 OUTPUT:-


<img width="455" height="276" alt="Customer-wise Order Summary Output" src="https://github.com/user-attachments/assets/b4dda5fa-5102-42ce-8d24-971cb1ae25fe" />



🟠 Customers With Above-Average Spending


    
💎 Query


<img width="455" height="242" alt="Customers with Above average Spending Query" src="https://github.com/user-attachments/assets/aac3a218-fece-45a6-8617-99aa16a86637" />



💎 Output


<img width="462" height="291" alt="Customers with Above average Spending Output" src="https://github.com/user-attachments/assets/4527a460-6545-404f-83c1-f861c76283b0" />



```

## Learning Outcomes

Through this project, I practiced:

- Writing SQL queries for business analysis
- Calculating customer-level revenue metrics
- Identifying high-value customers
- Calculating average order value correctly at the order level
- Using aggregate functions and grouped calculations
- Applying subqueries for comparative analysis
- Converting raw sales records into useful business insights
- Documenting a SQL project professionally on GitHub

## Future Improvements

Possible improvements for this project include:

- Adding region-wise sales analysis
- Analyzing sales by product category and sub-category
- Identifying the best-selling products
- Calculating monthly and yearly revenue trends
- Segmenting customers into high-, medium-, and low-value groups
- Creating a Power BI dashboard using the SQL analysis output
- Adding more advanced SQL concepts such as Common Table Expressions (CTEs), window functions, and customer ranking

## Assignment Details

- **Organization:** SkillNexis
- **Program:** Data Analytics Internship
- **Assignment:** Week 2 – SQL Customer and Order Analysis
- **Database Tool:** MySQL / MySQL Workbench
- **Focus Area:** Customer spending, order analysis, and sales insights

## Author

**Mukesh Samarit**  
Aspiring Data Analyst | Excel | SQL | Power BI | Tableau

- GitHub: [MSDIAN124](https://github.com/MSDIAN124)
- LinkedIn: www.linkedin.com/in/mukesh-samarit



## Note

This project was created for learning and internship-assignment purposes. The database and customer information used in this project are sample data only.
