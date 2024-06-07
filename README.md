# The datasets are from a unnamed business' online retail sales.  Lets help them out with some informative kernels and visualizations! Anything and everything helps! Includes online sales, profit, units sold, shipping, returns, time of order, and more!

# Organizing Data
-There were null rows in product type column. 'Unkown' is written for those unkown categories. The dash in the returns column and discounts column were deleted as well to not to get the false calculations.

# Sales Performance Q1
-What are the total gross sales, discounts, and net sales by product type?



Firstly, below SQL command was used to gather data to answer the question. Also, the numbers are adjusted to display numbers in thousands with two decimal places:
```SQL
SELECT 
    product_type,
    ROUND(SUM(gross_sales) / 1000, 2) AS Total_Gross_Sales_Thousands,
    ROUND(SUM(discounts) / 1000, 2) AS Total_Discounts_Thousands,
    ROUND(SUM(total_net_sales) / 1000, 2) AS Total_Net_Sales_Thousands
FROM 
    `Online_Business_Sales.retailsalescleaned`
GROUP BY 
product_type
```
The Result is:

<img width="861" alt="Screenshot 2024-06-07 at 18 33 17" src="https://github.com/esengok/Bellabeat-Case-Study/assets/169263106/f03834df-3e6a-45f6-83fe-aa9211e8fef5">

There were 19 product categories.






# Sales Performance Q2
-What is the return rate for each product type?

SQL Calculation: Return Rate = (Returns / Gross Sales) * 100 

```SQL
SELECT 
    product_type,
    ROUND(SUM(returns) / 1000, 2) AS total_returns,
    ROUND(SUM(gross_sales) / 1000, 2) AS total_gross_sales,
    ROUND((SUM(returns) / NULLIF(SUM(gross_sales), 0)) * 100, 2) AS return_rate_percentage
FROM 
    `logical-acumen-422709-f9.Online_Business_Sales.retailsalescleaned`
GROUP BY 
    product_type
```

The result is:

<img width="631" alt="Screenshot 2024-06-07 at 18 38 47" src="https://github.com/esengok/Bellabeat-Case-Study/assets/169263106/dc1e2221-d14e-4b5a-bb4f-88af9271f66a">


--------------------------------

# Sales Performance Q3
-Which product types have the highest and lowest net quantity sold?

```SQL
SELECT
product_type, 
SUM(net_quantity) AS total_net_quantity

FROM `Online_Business_Sales.retailsalescleaned`

GROUP BY product_type
ORDER BY total_net_quantity DESC
```
The result is:

<img width="436" alt="Screenshot 2024-06-07 at 18 50 14" src="https://github.com/esengok/Bellabeat-Case-Study/assets/169263106/9a54ac08-73fe-437c-a5f8-63a073ceb47e">




# Sales Performance Q4
Profitability Analysis
-What is the profit margin for each product type?

SQL Calculation: Profit Margin = ((Total Net Sales - Returns) / Gross Sales) * 100
```SQL
SELECT 
    product_type,
    ROUND(SUM(gross_sales)/ 1000, 2) AS Total_Gross_Sales,
    ROUND(SUM(returns) / 1000, 2) AS Total_Returns,
    ROUND(SUM(total_net_sales) / 1000, 2) AS Total_Net_Sales,
    ROUND(((SUM(total_net_sales) - SUM(returns)) / NULLIF(SUM(Gross_Sales), 0)) * 100, 2) AS Profit_Margin_Percentage
FROM 
    `logical-acumen-422709-f9.Online_Business_Sales.retailsalescleaned`
GROUP BY 
product_type
```
The result is:

<img width="777" alt="Screenshot 2024-06-07 at 18 59 18" src="https://github.com/esengok/Bellabeat-Case-Study/assets/169263106/f615a9a0-cc18-43ba-b975-cf925c5aa322">




# Sales Performance Q5
-How do discounts impact net sales across different product types?
```SQL
SELECT 
    Product_Type,
    ROUND(SUM(discounts) / 1000, 2) AS Total_Discounts,
    ROUND(SUM(total_net_sales) / 1000, 2) AS Total_Net_Sales
FROM 
    `logical-acumen-422709-f9.Online_Business_Sales.retailsalescleaned`
GROUP BY 
    Product_Type
```
The result is

<img width="586" alt="Screenshot 2024-06-07 at 19 14 15" src="https://github.com/esengok/Bellabeat-Case-Study/assets/169263106/766cc3f4-9535-4b34-8347-7f4e32ea59f8">

# Result and Recommendations

<img width="1052" alt="Screenshot 2024-06-07 at 20 13 10" src="https://github.com/esengok/Bellabeat-Case-Study/assets/169263106/16d6f35e-0881-4aaf-a285-0294c07f2da1">






