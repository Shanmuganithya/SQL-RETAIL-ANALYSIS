#  Sales Analysis Project

This project is a **Sales Data Analysis** conducted using **SQL**. It focuses on extracting meaningful business insights from raw transactional data. This is ideal for understanding sales performance, identifying trends, and supporting decision-making.

##  Project Files

- `SALES ANALYSIS.sql`: Contains all the SQL queries used for analyzing the sales data.

##  Key Analyses Performed

-  Calculated total revenue generated
-  Counted total quantity of products sold
-  Counted total number of unique orders
-  Found average revenue per order
-  Analyzed monthly sales trends
-  Identified the most selling product
-  Retrieved top 5 selling products by quantity
-  Retrieved top 5 products by revenue
-  Identified top 5 customers by total spending
-  Analyzed revenue generated by country
---

## SQL Queries

**Q.1) WRITE A SQL QUERY TO RETRIEVE ALL COLUMNS FOR SALES MADE ON "2022-11-05"**
'''SELECT ROUND(SUM(total_price), 2) AS Total_Revenue FROM sales;'''

** Q.2)WRITE A SQL QUERY TO RETRIEVE ALL TRANSACTIONS WERE THE CATEGORY IS "CLOTHING" AND THE QUANTITY SOLD IS MORE THAN 10 IN THE MONTH OF NOV-22**
'''SELECT 
FROM retail_sales
WHERE
category="CLOTHING" AND QUANTIY >=4 AND sale_date between "2022-11-01"AND"2022-11-30";
'''

**Q.3)WRITE A SQL QUERY TO CALCULATE THE TOTAL SALES (TOTAL_SALE) FOR EACH CATEGORY**
'''SELECT 
CATEGORY, 
SUM(TOTAL_SALE),
COUNT(*) AS 
TOTAL_ORDERS
FROM 
retail_sales group by category;
'''
**Q.4)WRITE A SQL QUERY TO FIND THE AVERAGE AGE OF CUSTOMERS WHO PURCHASED ITEMS FROM THE "BEAUTY" CATEGORY**
'''SELECT
round(AVG(AGE)) AS AVERAGE_AGE 
FROM
retail_sales WHERE category="BEAUTY";
'''

**Q.5)WRITE A SQL QUERY TO FIND ALL TRANSACTIONS WHERE THE TOTAL_SALES IS GREATER THAN 1000**
'''SELECT * 
FROM 
retail_sales WHERE total_sale > 1000;
'''

 **Q.6)WRITE A SQL QUERY TO FIND THE TOTAL NUMBER OF TRANSACTIONS (TRANSACTION_ID) MADE BY EACH GENDER IN EACH CATEGORY**
'''SELECT 
COUNT(TRANSACTIONS_ID),
GENDER,
CATEGORY
FROM 
retail_sales group by CATEGORY,GENDER;
'''

**Q.7)WRITE A SQL QUERY TO CALCULATE THE AVERAGE SALE FOR EACH MONTH.FIND OUT BEST SELLING MONTH IN EACH YEAR**
'''SELECT * FROM retail_sales;
select
    year,
	month,
    avg_sale
from
( 
SELECT 
     year(sale_date) as year ,
     month(SALE_DATE) AS MONTH,
     round(avg(total_sale)) as avg_sale,
	rank()  over(partition by year(sale_date) order by round(avg(total_sale)) desc) as ranks 
 FROM retail_sales
 GROUP BY year,month
 ) as t1
 where ranks = 1 ;'''

**Q.8) WRITE A SQL QUERY TO FIND THE TOP 5 CUSTOMERS BASED ON THE HIGHEST TOTAL SALES**
 '''SELECT
 CUSTOMER_ID,
 sum(TOTAL_SALE) AS TOTAL_SALES  
 FROM 
 RETAIL_SALES group by CUSTOMER_ID ORDER BY TOTAL_SALES DESC LIMIT 5;
 '''
**Q.9) WRITE A SQL QUERY TO FIND THE NUMBER OF UNIQUE CUSTOMERS WHO PURCHASED ITEMS FOR EACH CATEGORY**
 '''SELECT 
 CATEGORY,
 COUNT(distinct CUSTOMER_ID) AS UNIQUE_CUSTOMERS 
 FROM 
 retail_sales GROUP BY category;
 '''

 ***Q.10) WRITE A SQL QUERY TO CREATE EACH SHIFT AND NUMBER OF ORDERS (EXAMPLE MORNING <=12, AFTERNOON BETWEEN 12 & 17 ,EVENING > 17)***
''' SELECT COUNT(TRANSACTIONS_ID),
SHIFT 
FROM 
(
SELECT *,
CASE
 WHEN HOUR(SALE_TIME) < 12 THEN "MORNING"
 WHEN HOUR(SALE_TIME ) between 12 AND 17 THEN "AFTERNOON"
 ELSE "EVENING"
 END AS SHIFT
 FROM retail_sales
 ) AS T2 group by SHIFT;
 '''
 ##  Objectives

- Practice real-world SQL queries
- Perform data cleaning and transformation
- Generate actionable business insights

## How to Use

1. Open the `.sql` file in any SQL IDE (like MySQL Workbench).
2. Connect to your database and run the queries.
3. Ensure your dataset matches the schema expected by the queries.

## Notes

- You can extend the project by visualizing results using Power BI or Tableau.
- Dataset is assumed to be pre-loaded into the database. You can modify queries based on your table structure.

##  Contact

For questions or collaboration:  
**Shanmuganithya**  
 [nithyashan1030@gmail.com]

---

 *“Turning raw data into real insights!”*
